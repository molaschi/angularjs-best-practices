# AngularJS best practices 

*Hints and tips for large AngularJS applications*

This guide is based on openmind team experience in large SPA based on AngularJS

##Project and code organization

http://cliffmeyers.com/blog/2013/4/21/code-organization-angularjs-javascript
http://trochette.github.io/Angular-Design-Patterns-Best-Practices/#/intro

In a large project, AngularJS code could be logically splitted in 2 parts
- **core**: All the code needed at startup or shared by more than a single feature.<br/>Ideally, the code organization of the core follows a module-based criteria; usually modules are defined in a type-based criteria, ending in a project organized as follows:
```
/core
  /controllers
    login.ctrl.js
    error.ctrl.js
  /services
    cache.srv.js
    store.srv.js
    mail.srv.js
  /filters
    currency.flt.js
  /directives 
```

- **features**: Every application feature ("page") has its own folder, with specific controllers, services, filters, directives and views 
```
/features
  /homepage
    homepage.ctrl.js
    homepage.srv.js
    homepage.tmpl.html    
  /about
	about.ctrl.js
    about.tmpl.html
  /books
    books.ctrl.js
    books.tmpl.html
    books.show.tmpl.html
```

This code organizations helps you defining concatenation and minification rules in order to output a single javascript file for the whole core and one javascript file for every feature.

### Naming convention

In order to help you searching and defining build rules, suffix your files with the code type:
- controller: \*.ctrl.js
- service: \*.srv.js
- filter: \*.flt.js
- directive: \*.drv.js
- template: \*.tmpl.html

### AMD

If you use AMD in your project, there are some changes to files organization that ease AMD modules <-> AngularJS modules definition and loading:
```
/core
  index.js
  /controllers
    ...
    index.js
    module.js
  /services
    ...
    index.js
    module.js
  /filters
    ...
    index.js
    module.js
  /directives
    ...
    index.js
    module.js
/features
  /homepage
    index.js
    ...
  /about
    index.js
    ...
```

Add an *index.js* file to each folder to define dependency from subfolders or files.

**/core/index.js**
```
define([
  './controllers/index',
  './services/index',
  './filters/index',
  './directives/index'
], function () {
});
```

**/core/controllers/index.js**
```
define([
  './login.ctrl',
  './error.ctrl'
], function (angular) {
});
```

Following the module-based organization criteria, add to each module folder a *module.js* file in which the angular module is defined.

**/core/controllers/module.js**
```
define([
  'angular',
  '../services/index',
  '../filters/index',
  '../directives/index'
], function (angular) {
  return angular.module('myapp.controllers', [
    'myapp.services',
    'myapp.filters',
    'myapp.directives'
  ]);
});
```

Then make each controller / service / filter / directive dependant on the right module.js file:

**/core/controllers/\*.ctrl.js**
```
define([
  './module'
], function (module) {
  module.controller(...)
});
```

## Controllers

"Controller as" syntax let us to avoid injecting $scope for data binding.
http://toddmotto.com/digging-into-angulars-controller-as-syntax/
(http://blog.thoughtram.io/angularjs/2015/01/02/exploring-angular-1.3-bindToController.html)

Controller decoration to add $watch $on $broadcast and so on without $scope injection
http://plnkr.co/edit/PzPjYhtuopKvlwiVsYhT?p=preview

**Directives**
Short but clear explaination about directive lifecycle.
http://filimanjaro.com/blog/2014/angular-directive-lifecycle-vs-link-compile-controller/
http://www.jvandemo.com/the-nitty-gritty-of-compile-and-link-functions-inside-angularjs-directives/


**Misc.**
Performance tips for item lists
http://tech.small-improvements.com/2013/09/10/angularjs-performance-with-large-lists/



- debuginfoenabled = false su $compileProvider
- direttive: compile eseguito una volta, link tutte le volte. terminal e priority. scope. controller as.
- service vs factory vs provider (http://stackoverflow.com/questions/14324451/angular-service-vs-angular-factory)
- ng-model-options (http://blog.thoughtram.io/angularjs/2014/10/19/exploring-angular-1.3-ng-model-options.html)
- ng-repeat (track by, ng-hide)
- ng-if vs ng-show/ng-hide
- apply vs digest (http://www.bennadel.com/blog/2595-using-scope-digest-as-a-performance-optimization-in-angularjs.htm)
- eventi (event.stopPropagation() quando possibile)
- evalAsync vs $timeout (http://stackoverflow.com/questions/17301572/angularjs-evalasync-vs-timeout e 
- applyAsync (soprattutto per raggruppare in cicli di digest le risposte delle chiamate ajax con $httpProvider http://blog.thoughtram.io/angularjs/2015/01/14/exploring-angular-1.3-speed-up-with-applyAsync.html)
- applyAync vs evalAsync (http://www.bennadel.com/blog/2751-scope-applyasync-vs-scope-evalasync-in-angularjs-1-3.htm)
- decorate $exceptionHandler
- use $log
- destroy (http://www.bennadel.com/blog/2548-don-t-forget-to-cancel-timeout-timers-in-your-destroy-events-in-angularjs.htm) jQuery $interval
- ng-hint
- bind once {{::var}}
- scope e $watch
- controller snelli https://scotch.io/tutorials/making-skinny-angularjs-controllers

**Struttura**
https://scotch.io/tutorials/angularjs-best-practices-directory-structure
- app
 - main.js
 - routes.js
 - core
  - services
   - service1.js
   - service2.js
   - ...
  - controllers
   - controller1.js
   - controller2.js
   - ...
  - filters
   - filter1.js
   - filter2.js
   - ...
  - directives
   - directive1.js
   - directive2.js
   - ...
  - partials
   - directive1.html
   - directive2.html
   - ...
 - features
  - home
   - homeController.js
   - homeService.js
   - homeController2.js
   - ...
  - page
   - pageController.js
   - pageService.js
   - ...
