Integration
=====================================


Use with Angular CLI
-----------------------------------------------------------------

Installing @angular/cli
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*Note*: you can skip this part if you already have application generated.

```bash
npm install -g @angular/cli
ng new my-app
cd my-app
```

Add angular-froala-wysiwyg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- install `angular-froala-wysiwyg`

```bash
npm install angular-froala-wysiwyg --save
```

- open `src/app/app.module.ts` and add

```typescript
// Import all Froala Editor plugins.
// import 'froala-editor/js/plugins.pkgd.min.js';

// Import a single Froala Editor plugin.
// import 'froala-editor/js/plugins/align.min.js';

// Import a Froala Editor language file.
// import 'froala-editor/js/languages/de.js';

// Import Angular plugin.
import { FroalaEditorModule, FroalaViewModule } from 'angular-froala-wysiwyg';
...

@NgModule({
   ...
   imports: [FroalaEditorModule.forRoot(), FroalaViewModule.forRoot() ... ],
   ...
})
```

- open `angular.json` file and insert a new entry into the `styles` array

```json
"styles": [
  "styles.css",
  "./node_modules/froala-editor/css/froala_editor.pkgd.min.css",
  "./node_modules/froala-editor/css/froala_style.min.css",
]
```

- open `src/app/app.component.html` and add

```html
<div [froalaEditor]>Hello, Froala!</div>
```

Run angular-cli
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

```bash
ng serve
```



Use with `ionic v2 or v3`
-----------------------------------------------------------------


Create Ionic app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


*Note*: you can skip this part if you already have application generated.

```bash
npm install -g cordova ionic
ionic start sample blank
cd sample
```

Add angular-froala-wysiwyg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


For v3 make sure that you use the latest version of ionic and also the latest version of angular.

Installing Froala Wysiwyg Editor in Ionic is fairly easy, it can be done using npm:
```bash
npm install angular-froala-wysiwyg --save
```

- Inside `src/app/app.component.html` add

```html
<ion-app>
<ion-router-outlet></ion-router-outlet>
<div [froalaEditor]>Hello, Froala!</div>
</ion-app>
```


- open `src/app/app.module.ts` and add

```typescript
// Import all Froala Editor plugins.
// import 'froala-editor/js/plugins.pkgd.min.js';

// Import a single Froala Editor plugin.
// import 'froala-editor/js/plugins/align.min.js';

// Import a Froala Editor language file.
// import 'froala-editor/js/languages/de.js';

// Import Angular2 plugin.
import { FroalaEditorModule, FroalaViewModule } from 'angular-froala-wysiwyg';
...

```
Replace
```
imports: [BrowserModule, IonicModule.forRoot(), AppRoutingModule]
```
with
```
imports: [BrowserModule, IonicModule.forRoot(), AppRoutingModule,FroalaEditorModule.forRoot(), FroalaViewModule.forRoot()]
```

- Inside `src/app/app-routing.module.ts` remove the line
```
{ path: '', redirectTo: 'home', pathMatch: 'full' }
```

- Inside `src/index.html`

```html
<link rel="stylesheet" href="assets/css/font-awesome.min.css">
<link rel="stylesheet" href="assets/css/froala_editor.pkgd.min.css">
<link rel="stylesheet" href="assets/css/froala_style.min.css">
```

- In `angular.json` change outpath of build to  "outputPath": "src/assets" and insert following inside assets of build:
```javascript
  {
    "glob": "**/*",
    "input": "node_modules/froala-editor/css",
    "output": "css"
  },
  {
    "glob": "**/*",
    "input": "node_modules/font-awesome/css",
    "output": "css"
  },
  {
    "glob": "**/*",
    "input": "node_modules/font-awesome/fonts",
    "output": "fonts"
  },
  {
    "glob": "**/*",
    "input": "node_modules/froala-editor/js",
    "output": "js"
  }
```

Run your App
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


```bash
ionic build
ionic serve
```



Use with `webpack`
-----------------------------------------------------------------


Create webpack app

*Note*: you can skip this part if you already have application generated.

```bash
git clone --depth 1 https://github.com/AngularClass/angular-starter.git
cd angular-starter
npm install
npm install rxjs@6.0.0 --save
npm install @types/node@10.1.4
```

Add angular-froala-wysiwyg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


- install `angular-froala-wysiwyg`

```bash
npm install angular-froala-wysiwyg --save
```

- open `src/app/app.module.ts` and add

```typescript
// Import all Froala Editor plugins.
// import 'froala-editor/js/plugins.pkgd.min.js';

// Import a single Froala Editor plugin.
// import 'froala-editor/js/plugins/align.min.js';

// Import a Froala Editor language file.
// import 'froala-editor/js/languages/de.js';

// Import Angular plugin.
import { FroalaEditorModule, FroalaViewModule } from 'angular-froala-wysiwyg';
...

@NgModule({
   ...
   imports: [FroalaEditorModule.forRoot(), FroalaViewModule.forRoot(), ... ],
   ...
})
```

- open `src/app/app.component.ts` and add to the template

```html
<div [froalaEditor]>Hello, Froala!</div>
```

- open `config/webpack.common.js`

```javascript
var webpack = require('webpack');
```


- open `config/webpack.common.js` and add the following to `CopyWebpackPlugin`

```javascript
{
  from: 'node_modules/froala-editor/css/',
  to: 'assets/froala-editor/css/',
},
```

- open `config/head-config.common.js` and add a new entry to link

```javascript
{ rel: 'stylesheet', href: '/assets/froala-editor/css/froala_editor.pkgd.min.css' },
{ rel: 'stylesheet', href: '/assets/froala-editor/css/froala_style.min.css' }
```

Run webpack app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


```bash
npm run start
```



Use with `angular-seed`
-----------------------------------------------------------------


Create angular-seed app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


*Note*: you can skip this part if you already have application generated. For more details please also read: https://github.com/mgechev/angular-seed.

```bash
git clone --depth 1 https://github.com/mgechev/angular-seed.git
cd angular-seed
npm install
```

Add angular-froala-wysiwyg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


- install `angular-froala-wysiwyg`

```bash
npm install angular-froala-wysiwyg --save
```

- open `tools/config/project.config.ts` file and **uncomment** the following line from the top of the file

```typescript
import { ExtendPackages } from './seed.config.interfaces';
```

- in `tools/config/project.config.ts` file add

```typescript
...

this.NPM_DEPENDENCIES = [
  ...this.NPM_DEPENDENCIES,
  { src: 'froala-editor/css/froala_editor.pkgd.min.css', inject: true },
  { src: 'froala-editor/css/froala_style.min.css', inject: true }
];

...

let additionalPackages: ExtendPackages[] = [
  // required for dev build
  {
    name:'angular-froala-wysiwyg',
    path:'node_modules/angular-froala-wysiwyg/bundles/angular-froala-wysiwyg.umd.min.js'
  },

  // required for prod build
  {
    name:'angular-froala-wysiwyg/*',
    path:'node_modules/angular-froala-wysiwyg/bundles/angular-froala-wysiwyg.umd.min.js'
  }
]

this.addPackagesBundles(additionalPackages);
```

- open `src/client/app/home/home.module.ts` and add

```typescript
// Import all Froala Editor plugins.
// import 'froala-editor/js/plugins.pkgd.min.js';

// Import a single Froala Editor plugin.
// import 'froala-editor/js/plugins/align.min.js';

// Import a Froala Editor language file.
// import 'froala-editor/js/languages/de.js';

// Import Angular2 plugin.
import { FroalaEditorModule, FroalaViewModule } from 'angular-froala-wysiwyg';
...

@NgModule({
   ...
   imports: [FroalaEditorModule.forRoot(), FroalaViewModule.forRoot() ... ],
   ...
})
```

- open `src/client/app/home/home.component.html` and add

```html
<div [froalaEditor]>Hello, Froala!</div>
```

Run webpack app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


```bash
npm run start
```



Use with `system.js` and `JIT`
-----------------------------------------------------------------


Create Angular app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


*Note*: you can skip this part if you already have application generated.

```bash
git clone https://github.com/angular/quickstart.git angular-quickstart
cd angular-quickstart
npm install
```

Add angular-froala-wysiwyg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


- install `angular-froala-wysiwyg`

```bash
npm install angular-froala-wysiwyg --save
```

- open `src/index.html` and add

```html
<link rel="stylesheet" href="node_modules/froala-editor/css/froala_editor.pkgd.min.css">
<link rel="stylesheet" href="node_modules/froala-editor/css/froala_style.min.css">
```

- open `src/app/app.module.ts` and add

```typescript
// Import all Froala Editor plugins.
// import 'froala-editor/js/plugins.pkgd.min.js';

// Import a single Froala Editor plugin.
// import 'froala-editor/js/plugins/align.min.js';

// Import a Froala Editor language file.
// import 'froala-editor/js/languages/de.js';

// Import Angular2 plugin.
import { FroalaEditorModule, FroalaViewModule } from 'angular-froala-wysiwyg';
...

@NgModule({
   ...
   imports: [FroalaEditorModule.forRoot(), FroalaViewModule.forRoot(), ... ],
   ...
})
```

- open `src/app/app.component.ts` file and add to the template

```html
<div [froalaEditor]>Hello, Froala!</div>
```

- open `src/systemjs.config.js` file and add to map

```javascript
map: {
  ...
  'angular-froala-wysiwyg': 'npm:angular-froala-wysiwyg/bundles/angular-froala-wysiwyg.umd.js',
  ...
}
```

-

Run app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


```bash
npm run start
```



Use with `aot`
-----------------------------------------------------------------


Create Angular app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


1. ng new froala-aot

2. npm install font-awesome

3. npm install froala-editor

- Go to `angular.json` and change `architect.build.outputPath` to `src/dist` and add following code to `architect.build.options.assets`
```javascript
{
  "glob": "**/*",
  "input": "./node_modules/froala-editor",
  "output": "assets/froala-editor/"
},
{
  "glob": "**/*",
  "input": "./node_modules/font-awesome",
  "output": "assets/font-awesome/"
},
{
  "glob": "**/*",
  "input": "./node_modules/jquery",
  "output": "assets/jquery/"
}
```
- Go to `package.json` and update `scripts.build` to `ng build --aot` and `scripts.start` to `ng serve --aot`

Add angular-froala-wysiwyg
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


- install `angular-froala-wysiwyg`

```bash
npm install angular-froala-wysiwyg --save
```

- open `src/index.html` and add

```html
<link rel="stylesheet" href="assets/font-awesome/css/font-awesome.min.css">
<link rel="stylesheet" href="assets/froala-editor/css/froala_editor.pkgd.min.css">
```

- open `src/app/app.module.ts` and add

```typescript
// Import all Froala Editor plugins.
// import 'froala-editor/js/plugins.pkgd.min.js';

// Import a single Froala Editor plugin.
// import 'froala-editor/js/plugins/align.min.js';

// Import a Froala Editor language file.
// import 'froala-editor/js/languages/de.js';

// Import Angular2 plugin.
import { FroalaEditorModule, FroalaViewModule } from 'angular-froala-wysiwyg';
...

@NgModule({
   ...
   imports: [FroalaEditorModule.forRoot(), FroalaViewModule.forRoot(), ... ],
   ...
})
```

- open `src/app/app.component.ts` file and add to the template

```html
<div [froalaEditor]>Hello, Froala!</div>
```

Run app
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


```bash
npm run build
npm run start
```
