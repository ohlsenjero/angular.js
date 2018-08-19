Remember to install and run npm http-server!

-As it may be guessed, these "days", do not truly represent 24 hours, but a fraction of that time as it became available to me on those days. 

-Also, some things that I came across where addded on a previous day, so as to avoid jumping from one topic to another, and back

-what follows is a rather extensive document on my impressions (and toughts) as these came about. For a shorter version simply skip to the end where I summarize it all in a few sentences. 

___________________________________________________________________________________
____________________________________________________________________

day 1:16th


So first things first, I had never used Angular before, so I figured the best resource to learn about it would be their own platform


Luckily I was already familiar with some things, like npm and the "moustache" syntax present in app.component.html


I followed through the "Hello World" app, and then it was time for the "Tour of Heroes"..

But first I had to understand the folder/file structure, along with the file extensions used

In order to get more familiar with Angular, now that I had the very, bare bone, basics, I set up a few videos from trusted sources to get a look at the bigger picture, since, after all, Angular uses a lot more files and directories than I was used to with my NODE apps. 


So now it was time for the, so called, Tour of Heroes that would hopefully explain how to fetch a JSON file, or any other type of file for that matter.


----------------------------------

The implications get bigger and bigger, 

I understand about the test modules, components and environments.. or at least acknowledge their instances and declarations.

Clarifications dispersed within a TestBed...


..Later on Angular there are input arrays, provider arrays, and many other squary brackets. 


____________________________________________________________________


Now I'm starting to understand about boostrapped components, app-root\ appModule, and where @angular/core could lead to...

root Component;;App component



So what's Ng anyway? (sounds oddly familiar..  np..m

 
___________________________________________________________________________________
____________________________________________________________________

day 2:


it seems that Angular $http would be some sort of equivalent to jQuery's $.ajax

That's good


I find there's both Angular and Angujar.js

... ... ...


-Read brief again >>  it's angular.js


well... that should make it a bit easier, I suppose




And now I'm looking at the Angularjs.org official documentation. 

--
trying to get JSON file: 

Access-Control-Allow-Origin..
.. JSONP.. CORS?

I guess I need some sort of server..


I might as well do it by typing the content in the JSON file in.. having at least the front-end ready

downloaded JSON to local folder:

"Cross origin requests are only supported for protocol schemes: http, data, chrome, chrome-extension, https".

So I need to run this on the server??

but both Angular and Angujarjs are incapable of it??


npm http-server

$http.get runnig succesfully, 
Error (404): "Not Found"

...success(function(..data[1].author

for a while I couldn't get it to display on the HTML, but finally:

<tr ng-repeat="item in response">
       <td>{{item.author}}</td>

rather than {{response[item].author}} (even though {{response[0||1||2].author}} does work)


So apparently, I need to run this from a server to allow for Access-Control when grabbing that JSON remotely, or avoid "Cross origin requests are only supported for protocol schemes" error when fetching the data from a local folder, which is basically the same thing >> I need a server. 
Otherwise I can grab the files locally using http-server package/module instead, but only locally, which I guess is handy for production and a quick setup

 

___________________________________________________________________________________
____________________________________________________________________

days 3-4:

understanding ng + a few definitions::

===

"The ng module is loaded by default when an AngularJS application is started. The module itself contains the essential components for an AngularJS application to function."

so Module: collection of services, directives, controllers, filters, and configuration information...

ng-App & -repeat are (namespace) "Directives >> extended HTML attributes, prexix ng- >> in-built << add features to page <<<<<<<<   markers on DOM elements

"They teach the browser new syntax >>> directives are constructs << control structure/flow (statements are executed or not) <<<
 "syntactically allowable part of a program that may be formed from one or more lexical tokens in accordance with the rules of a programming language"
-sequences
-selection
-repetition


-repeat does that: repeat HTML elements (once forEach), whereas -app tells Angular where the app is to be (in the HTML) defining/preparing the Angujarjs app << outlining the "root element".

Now,  
ng-controller: JS object containing attributes/properties and functions. Each controller accepts $scope as a parameter which refers to the application/module that controller is to control.
But, what about "data-ng-controller??

some answers:

IE8 compatibility??  Thanks IE.

-"data- will allow the HTML to pass validation.. ?

- "Both data- and x- are html5 custom attribute naming compliant"

So at least on Chrome it works jsut the same either way. 



it woudl help to read a bit about MVC at this point.

.. so LAMP was cool, but this would come to fit in the MEAN stack. Cool, cool, I like Mongo, and Express, and I guess this is what I was missing (although ejs and handlebars worked quite alright), still, this seems to simplify DOM manipulation and ajax calls. 
Probably the same could be said about "partials" when it comes to controllers and their scope. 

"[angularJS] handles all of the DOM and AJAX glue code you once wrote by hand and puts it in a well-defined structure"


next on my list, $http & $scope

so $scope, as seen above, "refers to the application/module the controller is to control".
Like so: function whateverController($scope, __ 


----_---_--_-_--_---_----


"However, since HTML is case-insensitive, we refer to directives in the DOM by lower-case forms, typically using dash-delimited attributes on DOM elements (e.g. ng-model)."

... kebab-case vs camelCase


___________________________________________________________________________________
____________________________________________________________________


day 4:


Bidirectional Data Binding

changes in the model update the view and viceversa.


in Angular.js  "controller and model states are upheld within the client’s web browser" (rather than the server). 


so back at MVC. 

Model contains the data, the View presents it. Controller? negotiates between user and model...?

and that's where "scopes" come in >>  Namespaces >> applied as JS objects. 

one root scope + child scopes. 


Namespaces?

"set of symbols that are used to organize objects of various kinds, so that these objects may be referred to by name".
i.e.: file systems  << directories
                       /
commonly structured as hierarchies (rehuse names in different contexts)


"In essence, a namespace defines a scope."




$http

"AngularJS provides $http control which works as a service to read data from the server. $http is an AngularJS service for reading data from remote servers. The $http is a core AngularJS service that is used to communicate with the remote HTTP service via browser’s XMLHttpRequest object or via JSONP"

JSON vs JSONP?

"JSONP is a simple way to overcome browser restrictions when sending JSON responses from different domains from the client" 

("You essentially make a GET request with a callback parameter:

(get) http://api.example.com/endpoint?callback=foo
The server will wrap the JSON reply in a function call to your callback, where you can handle it:
foo({"your": "json", here: true})

There are some downsides, notably that JSONP only supports GET requests and that you still need a cooperative server").


....

"The $http service is a function that takes a configured object to generate a HTTP request and return the response. This response contains data, status code, header, configuration object and status text"

... which is why I have to grab the data as data.data rather

_
---------------------------------------------------

So I got the basics gowing, but now how do I choose what to populate on click, or ng-click.. 
I could have everything already loaded and hide/show the divs, but I guess that's not the idea (specially if the site were to get larger)


How do I dinamically change the ng-init setup on click?  I get the new values, but can't repopulate ng-repeat with them.

Also, trying to use a module gives me an error that the controller is not a function...
(sorted.. was closing the div before triggering what I needed)


so, following AngularJS tutorial now and should be fine from here on..



Duplicates in a repeater are not allowed. Use 'track by'...
track by $index will fix it,
but it also works fine if second ng-repeat comes from an array...


All working ok with ng-hide and show (although I suppose jQuery is less cumbersome there)

----------

but since the JSON data I'm grabbing already has it's HTML in there, I can't just push it in there as text. 

JSON.parse() alone throws "Unexpected token o in JSON at position 1"

but when combined with JSON.stringify, it all works well, 


so the functionality is finally there and now all I got to finish is the UI, adding Bootstrap


loaded a bunch of "external resources" from the docs.angularjs.org site to wrap up the first part of this learning trip. 


-_-_-_-_

Bootsrap
________
 

as far as I now is a set of pre-made JS funcions (using jQuery?) as well as CSS classes and such. 
Never really got into it since it required me to stop whatever project I was working on, in order to learn all of these new things, before continuing, when I could instead just get on to it with the tools I already had at hand. 
And also, because the one time I included the bootstrap CSS file, I saw myself chasing many of this already made styles which were getting on my way. 

But I guess it's pretty useful, if only to quickly add to whatever code that is already using it. 
And the alerts at least are pretty handy. 

..so take a look at the css file and see what classes I can use..

and the js..
and so on and so forth

So that's the thing, bootstrap.js seems to be nothing but a remake of certain aspects of jQuery, this or that way, which you could be using already with jQuery in the first place. Like everything today, being built up on top of something else, on top of something else.. ready to go code here + ready to go code there + all of this specs and docs and best-practices and concepts, to make your job faster.. right! but after you get around all of it, that is. 

it feels overkill at times, specially knowing which one of all these technologies to learn.. Should I learn Angular? or React? or Vue?  
Anyway, as they say: "necessity is the mother of invention". In that sense, I'm glad I found a good enough reason to finally get around it. 


wait.. Sticky footer?  
Now I'm starting to like this!

I guess, with a good doc beside you, it is a lot faster than typing all this CSS yourself (floating, clearfixing.. etc.. none of that anymore)

still, I already find myself going to the bootstrap.css file to change a few things. 
I like to work with percentages, rather than pixels for example. So you don't have to specify a @media for every possible resize.. and instead get onto that when it's truly necessary

also adding a bit or margin-top on "container-fluid"

line 826: li:  list-style: none, please, thank you. 

etc

I mean.. if you don't mind going back and forth to get rid of certain styles, it seems to be algood


So is this really faster?  If you want to use whatever someone else has made for you, yes. If you want to seemlessly add to it and build your own world, then it can also get in the way. 

I find it easier in the end to just write some styles on top of the basic bootstrap stuff.. 
Maybe something like Sass would be much more effective there.


Now let's add some bootstrap.js code, make it look semi=flash, and we're done


.collapse = .sideDown, and so on..


..well, I would like to add a crossfade, but for that I would need another set of <json-data>
<h2></h2><div></div><h4></h4>s to put the new stuff in, while keeping the old in and then delete it once the new has faded in on top (plus css-position:abosolute).. etc, etc. Not really necessary for the purposes of finishing this exercise

ok. So there's an issue on .resize. It behaves kinda funny when dragging the screen from the edges, rather than cliking on the "maximize" button, and .span2 doesn't look quite the same on firefox, but again, way beyond this exercise's scope. 
 

_____________
___________________________
____________________________________________
___________________________
_____________


So that's it. After reading from 1000 different sites and sources, I have the feeling I'm going to like AngularJS.
Seems like a straightforward enough way of manipulating DOM elements, as well as having the advantage of keeping everything in it's right place, regarding the resulting HTML structure, instead of having to chase after many ajax calls and functions which would be .appending stuff here and there, to the point that the initial html is only half of what's happening or is expected to happen, with all this empty divs waiting to be populated, who knows by which call 

This can aid the front-end, but then again, if you know how to deal with the back-end, I'm not  100% convinced it is any more practical than say, ejs on top of Node. But yes, definitely more practical to keep everything in check. 

Likewise, that ng-show/hide thing seems kinda unnecessary when you can use jQuery. 
But other things like ng-bind are great. In Node it would require some sort of convoluted Ajax way and back..  so I guess, just like with everything, some things are easier and others not so much. Just take what you need and leave the rest. 

Still, I got a lot more to read about, investigate and exercise before I truly get it. 
After I've done a few working sites I should have a much better idea of how to combine this with my prefered tools. And I guess it's a good introduction to move onto Angular and the whole typescript thing. 




