## Lesson 2:
I hope you had fun with lesson 1. Last time we looked briefly at AngularJS's DOM templating and `$scope` abstraction layer. This lesson is a closer look at how AngularJS's DOM Templating makes the view take control of the application. In AngularJS, the view displays information how it chooses instead of having the controller choose what information is inserted into which elements.

Take a look at the new index.html. There are some new things to mention:
 1. There is a new paragraph with `<span>In JSON that is </span>` and the `$scope.who` variable inside but the variable sure doesn't read like JSONN.
 2. There is a `<button>` that doesn't do anything labeled "Increment Counter" next to a `$scope.counter` variable.

### Expressions
Before we get to modifying those two, I would like to describe AngularJS's ability to handle expressions in the DOM templates. There are a great number of things you can put in those `{{ }}`. Of course we have already used simple variables like `{{ who }}` but we can put expressions and filters in there too.

Lets start by changing the `<h2>Hello {{ who }}!</h2>` to have something more colorful. Try `<h2>{{'Hello '+who+'!'}}</h2>`. That's right! the DOM templating can use literals and contaminators among other things.

Those expressions can also use filters in the same way Unix does, the | (pipe) command. In that paragraph with the span. change the `{{ who }}` to `{{ who | json }}`. The pipe works just like in Unix to pass the output of one command into the input of the next. the `json` filter outputs the JSON.stringify() of anything you give it. In this case there isn't much difference, but the `json` filter adds `""` around the `$scope.who` variable. Later we will have arrays and you can try this filter again to see the output. It is far more interesting.
There are other filters including orderBy, limitTo, and number, but we don't need to get into those quite yet. Feel free to experiment with them though.

Last we will go over a new directive, `ng-click=""`. Again if you want you can use `data-ng-click=""` where you are cautious of strict standards. `ng-click=""` does whatever you say whenever you click the element. No need for the element to be a button or anchor either. you can put `ng-click=""` on almost anything.
Add the `ng-click` to the `<button>` and put `counter = counter + 1` inside the `ng-click`. Now if you run the index.html, every time you click the button the counter variable increases. Notice that there is no controller to do this. There are no jQuery selectors or $.on() functions to call. The click updates the `$scope.counter` and AngularJS updates the DOM to match the new data.