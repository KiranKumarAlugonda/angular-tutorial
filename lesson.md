## Lesson 1:
If you're reading this, you're probably already convinced that AngularJS is worth a try and you wanna know all about it. So I won't try to convince you, but jump right in with the view.

Start by opening index.html. You will see angular is included into the bottom of the page, the `<body>` has `ng-app` as an attribute, and the header says hello to someone yet to be determined.

I want to mention the first two briefly:
 1. `ng-app` - this tells Angular where to start and what to initialize. Some browsers may not like the attribute (IE -- who else) so there are many other ways to use it in places you are concerned about passing strict standards, my favorite is `data-ng-app` but [here is a full list of others.](http://docs.angularjs.org/api/ng.directive:ngApp)
 2. `<script src="lib/angular.js"></script>` - The script is at the bottom of the page. This is standard best practice for all browsers -- [read more here.](http://developer.yahoo.com/performance/rules.html#js_bottom)

### Now lets say hello!
For the moment, the header just says `Hello !` and the input doesn't do anything.

Notice in the code, the header reads `{{ who }}`. This tag creates a variable in the `$scope` of this application: `$scope.who`. the `$scope` is an abstraction layer in the AngularJS application that manages data, bindings and all those little things we don't need to know about quite yet. If `$scope.who` is already set, `{{ who }}` will be replaced with the stringification of `$scope.who`. Otherwise AngularJS will just set `$scope.who` to equal `null`, which stringified is an empty string. Thus the output is `<h2>Hello !</h2>`.

In order to change `$scope.who` we need to bind something with an input to `$scope.who`. The `$scope` manages data-binding in both directions, setting variables and updating the DOM. The `ng-model` directive is used to bind an input to the `$scope`. Add `ng-model="who"` to the input and `$scope.who` will be updated whenever the input changes. the input should read `<input type="text" ng-model="who" />`.

When you run index.html you will be able to put any thing into the input and your HTML will say hello. Give it a try, say hello. It really is that easy, `ng-model="who"` links to {{ who }}!

### Summary
In this lesson we went over how AngularJS uses DOM templating to place date where you want it. Also, we touched base on the important concept of `$scope` and how AngularJS uses this abstraction layer to store information and to do all the nitty-gritty DOM manipulation that you don't have to do any longer.

Play around a little bit. Try creating new variables and try `{{ }}` in attributes. When you are ready progress to lesson-02 with `git checkout lesson-02` you will have to either commit changes or checkout index.html or you will get an warning.