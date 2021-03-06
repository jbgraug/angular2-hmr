# Angular 2 Hot Module Replacement
> Angular2-HMR


This module requires Angular 2.0.0-rc.1 or higher. Please see repository [Angular 2 Webpack Starter](https://github.com/angularclass/angular2-webpack-starter) for a working example. 

`main.browser.ts`
```typescript

function main(initialHMRstate) {
  // you must return
  return bootstrap(App, []);
}
/*
 * Hot Module Reload
 * experimental version by @gdi2290
 */
if (isDevelopment) {
  // activate hot module reload
  let ngHmr = require('angular2-hmr');
  ngHmr.hotModuleReplacement(main, module); // pass the main function
} else {
  // bootstrap when document is ready
  document.addEventListener('DOMContentLoaded', () => main());
}
```
`app.service.ts`
```typescript
import {HmrState} from 'angular2-hmr';

export class AppState {
  // @HmrState() is used by HMR to track the state of any object during a hot module replacement
  @HmrState() _state = { };
}
```

`app.component.ts`
```typescript
import {HmrState} from 'angular2-hmr';
@Component({ /*... */ })
export class App {

  @HmrState() localState = {};
    
}
```


In production set `NODE_ENV` to `"production"` to noop `HmrState` or strip it from your code
```typescript
    new NormalModuleReplacementPlugin(
      /angular2-hmr/,
      path.join(__dirname, 'node_modules', 'angular2-hmr', 'prod.js')
    ),
```



___

enjoy — **AngularClass**

<br><br>

[![AngularClass](https://cloud.githubusercontent.com/assets/1016365/9863770/cb0620fc-5af7-11e5-89df-d4b0b2cdfc43.png  "Angular Class")](https://angularclass.com)
##[AngularClass](https://angularclass.com)
> Learn AngularJS, Angular 2, and Modern Web Development from the best.
> Looking for corporate Angular training, want to host us, or Angular consulting? patrick@angularclass.com
