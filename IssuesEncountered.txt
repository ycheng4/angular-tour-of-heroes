Problems Encountered while doing this

1) Followed the guide here https://angular.io/docs/ts/latest/tutorial/toh-pt1.html and tried to convert to javascript. Encountered an error on this line when <input value="{{hero.name}}" placeholder="name">

Error :
	Can't bind to 'ngModel' since it isn't a known property of 'input'. (\"

Resolution :
Found that you had to import in the FormsModule

2) Proceeded to add in FormsModule into and got an error
- imports: [ ng.platformBrowser.BrowserModule,FormsModule]

Error :
[Error] ReferenceError: Can't find variable: FormsModule
	(anonymous function) (app.module.js:4)
	Global Code (app.module.js:11)
[Error] TypeError: undefined is not an object (evaluating 'typeOrFunc.annotations')
	runTask (zone.js:140)
	invoke (zone.js:304)

Resolution :
With abit of reference to https://angular.io/docs/ts/latest/api/ on BrowserModule that is an existing import from quick start, i figured out that @angular/platform-browser is equal to ng.platformBrowser.BrowserModule because

@angular = ng
platform-browser = platformBrowser

Under @angular/platform-browser was BrowserModule

the slash (/) in the case is as per normal converted to dot (.)

Using the same knowledge, i found that FormsModule is under @angular/forms so i converted it to ng.forms.FormsModule

3) After doing the above, i was still met with another error instead

Error :
	[Error] TypeError: undefined is not an object (evaluating 'ng.forms.FormsModule')
	(anonymous function) (app.module.js:4)
	Global Code (app.module.js:11)

Resolution :

Thinking that i forgot to import in a js file as normal angular, i decided to check index.html and found that platformBrowser had some umd.js file and went to find FormsModule.

<script src="node_modules/@angular/platform-browser/bundles/platform-browser.umd.js"></script>
<script src="node_modules/@angular/platform-browser-dynamic/bundles/platform-browser-dynamic.umd.js"></script>

Using the same logic, i found that FormsModule in node_modules and added this line

<script src="node_modules/@angular/forms/bundles/forms.umd.js"></script>

Part 1 was completed