# gulp-slate

node.js with port of tripit/slate to be included in gulp :)

## usage

### Instalation
```
npm install gulp-slate --save
```

### Gulp Setup

now you can setup a gulp task to handle the build
```
// inside of gulpfile.js
var gulp = require('gulp');
var slate = require('gulp-slate');

gulp.task('slate', function () {
    return gulp.src(
        [
            'node_modules/gulp-slate/node_modules/slate/source/index.html.md'
        ]
    )
        .pipe(slate())
        .pipe(gulp.dest('dist/'))
    ;
});
```

### First Build

this is really simple since the task is already setup:

```
gulp slate
```

now go on and host the dist/ folder somewhere

### simple webserver
```
python -m SimpleHTTPServer 8000
```

now open http://localhost:8000 in a browser of your choice, result should look exactly like http://tripit.github.io/slate/

### constructor(options)
#### options.assets
add assets to current stream

Type: `Boolean`<br><br>Default `true`

#### options.filename
set the filename - warning: only use one input file! else only the last one will show up

Type: `String`<br><br>Default `index.html.md` will become `index.html`

#### options.template
Template to render - in general you should never need to touch this

Type: `String`<br><br>Default `src/layout.html`

#### options.logo
to have a custom logo added to the page

Type: `String`<br><br>Default `node_modules/slate/source/images/logo.png`

#### options.includeLoader
where to load includes from, the function receives the name as well as the
path to the main markdown file and should return a promise that resolves the file content

Type: `Function`<br><br>Default `error` will be loaded from `includes/_error.md`

## thanks to
* https://github.com/jmanek/slate_node
* https://github.com/tripit/slate
