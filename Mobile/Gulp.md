#Gulp 

###Tuto : 
[Premiers pas](https://la-cascade.io/gulp-pour-les-debutants/)

###Code commenté : 

```
var gulp = require('gulp');
var gutil = require('gulp-util');
var bower = require('bower');
var concat = require('gulp-concat');
var sass = require('gulp-sass'); //Conversion des SCSS en CSS
var minifyCss = require('gulp-minify-css'); //Minification des CSS
var rename = require('gulp-rename'); // Renommage des fichiers 
var sh = require('shelljs');
 //SCSS TASK
var paths = {
  sass: ['./scss/**/*.scss']
};

gulp.task('default', ['sass']);

gulp.task('sass', function(done) {
  gulp.src('./scss/ionic.app.scss') //Prend en entrée les fichiers ionic.app.scss
    .pipe(sass())                   //Compile les fichiers 
    .on('error', sass.logError)
    .pipe(gulp.dest('./www/css/'))
    .pipe(minifyCss({               //Minifie le CSS qui a généré
      keepSpecialComments: 0
    }))
    .pipe(rename({ extname: '.min.css' }))  //Renomme le fichier 
    .pipe(gulp.dest('./www/css/'))          //Sauvegarde le tout dans /www/css/
    .on('end', done);
});

gulp.task('watch', ['sass'], function() { //Exécute la compilation à chaque modification du fichier SASS, ref var paths
  gulp.watch(paths.sass, ['sass']);
});

```

###Evaluation : 

Code dans le gulpfile.js
```
var gulp = require('gulp');

gulp.task('HelloWorld', function() {
	// body...
	console.log('Hello World :)');
});
```
Dans le .bash

```
loic.maupin@PC-DG-CAMPUS-21 MINGW64 /c/UwAmp/www/GulpTest
$ node_modules/gulp/bin/gulp.js HelloWorld
[09:48:33] Using gulpfile C:\UwAmp\www\GulpTest\gulpfile.js
[09:48:33] Starting 'HelloWorld'...
Hello World :)
[09:48:33] Finished 'HelloWorld' after 83 μs

```
