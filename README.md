# AngularJS best practices 

*Hints and tips for large AngularJS applications*

This guide is based on openmind team experience in large SPA based on AngularJS

##Project and code organization
In a large project, AngularJS code could be logically splitted in 2 main parts
- **core**
contains all the code needed at startup or shared by more than a single application feature. Ideally core part follow "by type" organization:
- features: containes all the code  
Large project organization need to follow a feature-based criteria. In every dir representing a feature we need to put a kind of JS manifest that includes all the objects used in that module. In the manifest we also add all the requireJS/browserifiy loading logic:
http://cliffmeyers.com/blog/2013/4/21/code-organization-angularjs-javascript

Various best practices for large projects:
http://trochette.github.io/Angular-Design-Patterns-Best-Practices/#/intro

**Controller**

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
