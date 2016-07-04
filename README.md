# Website Performance Optimization

To visit the hosted GitHub page navigate to http://diondlewis.github.io/webopt/. You can also download the project at https://github.com/diondlewis/webopt by cloning the prepository to your computer using Git or downloading the zip file.



##PageSpeed Score
index.html achieves a PageSpeed score of at least 90 for Mobile and Desktop.

#### Critical Rendering Path:

* Used Adobe Photoshop to resize and compress pizzaria.jpg
* Add a media query for print.css
* Minify CSS at https://cssminifier.com/
* Minify JavaScript at https://javascript-minifier.com/
* Make JavaScropt async
* Move Javascript tags to the bottom of the body

##Getting Rid of Jank
Optimizations made to views/js/main.js make views/pizza.html render with a consistent frame-rate at 60fps when scrolling.

#### Frame Rate:

* Move all constants out of the for loop in updatePositions
* Move the Math.sin calculation out for the for loop in updatePositions
* Move var items = document.getElementsByClassName('mover'); to the anonymous function at the bottom of the file to stop updatePositions from re-defining items on every scroll event
* Use window.items[i].style.left = items[i].basicLeft + 100 * phase + 'px'; instead of items
* Set number of pizzas to 36 in document.addEventListener('DOMContentLoaded', function()
* Replace "querySelector" with getElementById in document.getElementById("movingPizzas1").appendChild(elem);
* Switch to document.getElementById instead of document.querySelector in function determineDx
* Declare var phase outside the for loop on line 561 to prevent it from being created each iteration
* Declare var elem outside the loop on line 599 to prevent it being created each iteration
* Declare movingPizzas outside the for loop to prevent a DOM call on each iteration
* Change CSS for .mover: Add transform: translateZ(0); will-change: transform; transform translate3d(0,0,0); and backface-visibility: hidden;
* Use a transform on line 572 instead of window.items[i].style.left = items[i].basicLeft + 100 * phase + 'px';
* Replace animationReady check with updatePositions in this event listener: window.addEventListener('scroll', updatePositions);
* Calculate number of pizzas based on window size

#### Computational Efficiency:
Time to resize pizzas is less than 5 ms using the pizza size slider on the views/pizza.html page. Resize time is shown in the browser developer tools.

* Optimize Time to Resize Pizzas in pizza.html
* Made the following changes to changePizzaSizes:
* Move document.document.querySelectorAll(".randomPizzaContainer"); outside the for loop
* Refactor to use a switch to set pizza width in order to avoid Forced Synchronous Layout and avoid use of determineDx to determine new pizza widths
* Switch to document.getElementsByClassName from document.querySelectorAll in this line of changePizzaSizes
var randomPizzas = document.getElementsByClassName("randomPizzaContainer");
* Move randomPizzas.length to a local variable so the array's length property isn't accessed on each iteration
* Move var pizzasDiv = document.getElementById("randomPizzas"); out of the for loop on line 498 so the loop only makes one DOM call
* Change CSS for .randomPizzaContainer: Add transform: translateZ(0); and will-change: transform;
