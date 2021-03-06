# Vue Gulp Rollup [![CircleCI](https://circleci.com/gh/Sirikon/vue-gulp-rollup.svg?style=svg)](https://circleci.com/gh/Sirikon/vue-gulp-rollup) [![dev dependencies](https://david-dm.org/sirikon/vue-gulp-rollup/dev-status.svg)](https://david-dm.org/Sirikon/vue-gulp-rollup?type=dev) #

Example project which uses Vue (.vue files), Gulp and Rollup

## Build & Run ##

```bash
npm install

# Single build
npm run build

# Build and start watching for changes
npm run dev
```

## Technical Decisions ##

 - __Gulp and Rollup__: Because are simpler and fit my needs.
 - __Only using .vue files for javascript and template__: This is because having css/postcss/sass/less/whatever inside .vue files required some things I don't like:
   - Rollup plugin for Vue required some _not so clear_ code to get it working with SASS or LESS
   - Rollup plugin for Vue works nicely with CSS Modules, but at the moment I don't work with CSS Modules, and doesn't like at all the idea of `import clasNames from './style.css'`. 
 - __Library imports are fake__: Loading in memory and tree-shaking a library that is already lightweight and minified seems completely unnecesary. Not importing the library and using `gulp-concat` later is way more efficient and speeds up the development time taking down the compilation time.
 - __Vue's default config for ESLint__: I'm not fully convinced of the idea of 2 spaces instead of tabs, or prohibiting semicolons... but seems like it's the Vue's standard.
 - __Hot reload not included__: I'll not add more code to the build process just to avoid hitting F5.
 - __Static web server not included__: Useful for demos, mostly useless for real world, If you need it, use [http-server](https://www.npmjs.com/package/http-server) in CLI or npm script.
 - __Building-related files (gulpfile.js and everything inside gulp folder) MUST run as-is in Node (No transpilation required)__: It's just unnecessary, latest node versions already have arrow functions, classes and all that fancy syntactic sugar, and doing `require()` instead of `import` isn't THAT bad, deal with it.
 - __Bublé__: From my experience, it's much faster and simpler than Babel, and plays well with Rollup ([just see the plugin implementation](https://gitlab.com/Rich-Harris/rollup-plugin-buble/blob/master/src/index.js)).
 - __npm dependencies versions with just minor patches__: You already know what SEMVER is and what the world thinks SEMVER is, so better be a bit more secure.
 - __Dependencies should come only from NPM__: Don't accept a dependency that requires you to have things installed like Ruby or Python. Just Node.
 - __Build process must be cross platform__: Yes, that includes Windows.
 - __Focused to work on the latest Node LTS version__.

## License ##

```
MIT License

Copyright (c) 2017 Carlos Fernández

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
