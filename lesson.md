## Lesson 3:
Hello again, in this lesson we will talk about arrays, `ng-repeat=""` attribute, and child/sub `$scope`. These are probably the two most utilized features of AngularJS and you will be amazed at how easy it is to utilize them. 

Go ahead and open the new index.html. There are some more changes. The counter is gone, we won't need it for now, and there is a new `<ul>` and `<li>`. I have pre-populated the `<li>` with a `$scope.person` variable. On the `<li>` there is an `ng-repeat=""` attribute. Try entering something into the input. You will see both `{{ who }}` and `{{ who | json }}` update but person doesn't do anything because we don't have anything assigned to modify `$scope.person`.  

First, we will modify the `ng-model="who"` output so it forms an array instead of just a string. Add onto the input this attribute, `ng-list`. This makes the input string a comma separated, trimmed list and store it as an array in `$scope.who` ([More info here](http://docs.angularjs.org/api/ng.directive:ngList)). Go ahead and add the attribute then type something like `"John, Tom, Joe"` into the text field. You'll see the difference in the `{{ who }}` and `{{ who | json }}` outputs.

Next lets use this new array. Inside the `ng-repeat=""` add this string, `"person in who"`. This works just like forEach in multiple languages. The `ng-repeat` uses the node it sits on and its children as a template and produces one copy for each `person` in `$scope.who`. Try typing in some comma seperated names again and you will see that each person gets a hello. Also you can see that the names AND the number of people update automatically. This feature is done without writing any code for adding or removing `<li>` tags. 

Last, I want to describe the `$scope` in relation to what just happened with `ng-repeat`. Each of the children produced by `ng-repeat` get its own separate sub-scope. Just like in JavaScript or PHP, you can call `{{ who }}` of the parent `$scope` from inside the child `$scope`, but each child `$scope` is completely separate from the others. Later, we can get into arrays of objects and accessing the properties of those objects.

***
Next lesson, we will go over text-filtering, `orderBy`, and the `ng-init=""` attribute.