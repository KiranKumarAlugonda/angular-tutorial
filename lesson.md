## Lesson 4:
Hello again! In this lesson we'll go over some of the really cool functions of the view that we haven't yet discussed: String filtering, orderBy, ternary statements, and the `ng-init` attribute. I hope by now you are starting to see why the view is so powerful in AngularJS.

When you look at the new index.html you'll notice some major changes. The most noticeable change is the `ng-init` at the top -- I'll describe that later. Also, I got rid of the text field for `$scope.who` and replaced it with a text box bound to `$scope.showOnly`. Next there are two new buttons with `ng-click` attributes which change a variable named `$scope.sort`. Last, I changed the contents of the `<li>`.

### ng-init
`ng-init=""` -- This directive will run just after AngularJS reads the DOM elements into memory and before it starts replacing bound DOM elements with data or looping through `ng-repeat` attributes. As you can see in the example, it is usually used for initializing the default variables needed for that set of elements, but it can also call an initialization function or any number of other things that you might need to happen before a collection of DOM nodes is displayed. You may even put it inside an `ng-repeat` template. It will be called after AngularJS processes the template but before AngularJS starts executing the commands inside.
In this case, the `ng-init` is making our `$scope.who` variable ready.

### Object Properties
Go ahead and run the index.html. You will see empty hellos and not much else. That is because the `ng-repeat` is making an `<li>` for each person, but the templates inside aren't linked to any data. Start by replacing the first `{{  }}` with `{{ person }}`. You will see that this produces all the data on that person in a JSON format. Most people won't take the time to read the JSON string, so lets make it more user friendly. Have the list say hello to `{{ person.name }}`. You should recognize that `name` is one of the properties inside each of the `person` objects inside the `$scope.who` array we initialized with `ng-init`. Add age where it belongs using `{{ person.age }}`.

Now you can see clearly how the child `$scope` works. Each repetition of `ng-repeat` gets its own child `$scope` where `$scope.person` is instantiated with a `person.name` property and a `person.age` property. Each child `$scope` can access its own information and its parent `$scope` but not any of the others' -- sibling `$scope` if you will.

### Ternary Statement
You may have noticed that some people don't have ages and the statement, "Your age is ." looks incomplete. AngularJS won't support true ternary statements until [version 1.1.5](http://blog.angularjs.org/2013/05/angularjs-107-monochromatic-rainbow-and.html) (we get if statements then too). Until that time there is a way to short it using boolean conditional shorting A.K.A [Short Circuit Evaluation](http://en.wikipedia.org/wiki/Short-circuit_evaluation). Try this, `{{ person.age || 'not given' }}`. Just like in a standard boolean expression the first fails with a false-ish value (`null` in this case) and tries the next statement because the first is followed by an `||` (or) operator. The same concept works with `&&` (and) operators, `{{ false && explode() }}` will never `explode()`  because of the `&&` operator and short circuit evaluation.

### String Filter
Next, let's search for people we know by adding a `filter`. Add to the `ng-repeat` expression so it reads, `person in who | filter:showOnly`. This passes each `person` object into the `filter` before making that person's DOM elements. You may notice that the text box is also linked to `$scope.showOnly`. Try it out and see the reaction.
* If you enter "sa" into the text box, only Sarah, Samuel, Samantha, and Tessa appear in the list. 
* If you enter "2", Danial and Daniel are the only people displayed.

### orderBy
Last, let's utilize those two `<buttons>`. In the HTML you can see that each sets a variable, `$scope.sort`, to either 'name' or 'age' (notice those are the names of out `person` object properties). After the `... | filter:showOnly` add `... | orderBy:sort`. Then when you click either button it changes how we sort the list. `orderBy` only works when you have an array of objects to sort. You can even sort ascending or descending. Make the `orderBy` read like this `... | orderBy:sort:reverse` and instruct the buttons how to handle `reverse`, `sort = 'name'; reverse = !reverse` -- do the same with both buttons and the list will sort ascending and descending.


### Next Time:
Next time we'll finally get into controllers. I have done my best to impart the power of AngularJS's view. To be honest, I try to come up with new fun mini-projects with AngularJS that don't require any controller at all. So far my favorite is a working calculator.