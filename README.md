# angularjs-best-practices

**Project and code organization**

Large project organization need to follow a feature-based criteria. In every dir representing a feature we need to put a kind of JS manifest that includes all the objects used in that module. In the manifest we also add all the requireJS/browserifiy loading logic:
http://cliffmeyers.com/blog/2013/4/21/code-organization-angularjs-javascript

**Controller**

"Controller as" syntax let us to avoid injecting $scope for data binding.
http://toddmotto.com/digging-into-angulars-controller-as-syntax/

Controller decoration to add $watch $on $broadcast and so on without $scope injection
http://plnkr.co/edit/PzPjYhtuopKvlwiVsYhT?p=preview


