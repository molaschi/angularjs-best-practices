# angularjs-best-practices

**Project and code organization**

Large project organization need to follow a feature-based criteria. In every dir representing a feature we need to put a kind of JS manifest that includes all the objects used in that module. In the manifest we also add all the requireJS/browserifiy loading logic:
http://cliffmeyers.com/blog/2013/4/21/code-organization-angularjs-javascript

Various best practices for large projects:
http://trochette.github.io/Angular-Design-Patterns-Best-Practices/#/intro

**Controller**

"Controller as" syntax let us to avoid injecting $scope for data binding.
http://toddmotto.com/digging-into-angulars-controller-as-syntax/

Controller decoration to add $watch $on $broadcast and so on without $scope injection
http://plnkr.co/edit/PzPjYhtuopKvlwiVsYhT?p=preview

**Directives**
Short but clear explaination about directive lifecycle.
http://filimanjaro.com/blog/2014/angular-directive-lifecycle-vs-link-compile-controller/


**Misc.**
Performance tips for item lists
http://tech.small-improvements.com/2013/09/10/angularjs-performance-with-large-lists/



- service vs factory vs provider (http://stackoverflow.com/questions/14324451/angular-service-vs-angular-factory)
- ng-model-options (http://blog.thoughtram.io/angularjs/2014/10/19/exploring-angular-1.3-ng-model-options.html)
- ng-repeat (track by, ng-hide)
- ng-if vs ng-show/ng-hide
- apply vs digest (http://www.bennadel.com/blog/2595-using-scope-digest-as-a-performance-optimization-in-angularjs.htm)
- eventi
- evalAsync vs $timeout (http://stackoverflow.com/questions/17301572/angularjs-evalasync-vs-timeout e 
- applyAsync (soprattutto per raggruppare in cicli di digest le risposte delle chiamate ajax con $httpProvider http://blog.thoughtram.io/angularjs/2015/01/14/exploring-angular-1.3-speed-up-with-applyAsync.html)
- decorate $exceptionHandler
- use $log
- destroy (http://www.bennadel.com/blog/2548-don-t-forget-to-cancel-timeout-timers-in-your-destroy-events-in-angularjs.htm)
- ng-hint
- bind once {{::var}}