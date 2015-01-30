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