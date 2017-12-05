# Javascript tasks with gulp

Work to the <b>start</b> folder, the solutions are in the <b>end</b> folder

##  1. Uglify 
Minify (uglify) main.js and copy into web folder change its name to main.min.js

Declare gulp-uglify in your gulpfile.js

```
var uglify = require('gulp-uglify');
```

Declare some static variables

```
// static javascript variables
var srcMainJs = 'js/main.js';
var distMainJs = '../web/js';
var minMainJs = 'main.min.js';
```

Write the task

```
// Scripts
gulp.task('main-js', function(){
  return gulp.src(srcMainJs)
  .pipe(sourcemaps.init())
  .pipe(uglify())
  .pipe(concat(minMainJs))
  .pipe(sourcemaps.write('./maps'))
  .pipe(gulp.dest(distMainJs));
});
```

# 2. Reduce app requests 
vendor javascripts minify, and concat into one file, the new filename will be vendor.packs.min.js

Declare some static variables

```
// vendor static javascript variables
var distVendorJs = '../web/js/vendor';
var vendorJs = 'js/vendor/plugins/*.js';
var vendorPackJsMin = 'vendor.packs.min.js';
```

Write the task

```
gulp.task('vendor-js', function(){
  return gulp.src(vendorJs)
  .pipe(uglify())
  .pipe(concat(vendorPackJsMin))
  .pipe(gulp.dest(distVendorJs));
});
```

# 3.  Modify index.html
Bottom in index.html delete 7 js vendor links and put our vendor.packs.min.js link
