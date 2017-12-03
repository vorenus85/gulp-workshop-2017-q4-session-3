"# gulp-workshop-2017-q4-session-3"

# 1. Tömörítsük a main.js fájlunkat és másoljuk át a web mappába main.min.js néven

deklaráljuk az uglify csomagot

```
var uglify = require('gulp-uglify');
```

hozzuk létre a következő statikus változókat

```
// static javascript variables
var srcMainJs = 'js/main.js';
var distMainJs = '../web/js';
var minMainJs = 'main.min.js';
```

írjuk meg a taskot

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

# 2. Tömörítsük a vendor js és másoljuk át a web mappába vendor-pack.min.js néven

hozzuk létre a következő statikus változókat

```
// vendor static javascript variables
var distVendorJs = '../web/js/vendor';
var vendorJs = 'js/vendor/plugins/*.js';
var vendorPackJsMin = 'vendor.packs.min.js';
```

írjuk meg a taskot

```
gulp.task('vendor-js', function(){
  return gulp.src(vendorJs)
  .pipe(uglify())
  .pipe(concat(vendorPackJsMin))
  .pipe(gulp.dest(distVendorJs));
});
```

# 3. Az index.html alján töröljük a 7 vendor js taget, és húzzuk be a minify-olt fájlt
