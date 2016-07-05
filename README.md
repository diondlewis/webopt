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

* Move all constants and the Math.sin calculation out of the for loop in the updatePositions function

* Move variable items = document.getElementsByClassName() to the anonymous function at the bottom of the file to stop updatePositions from re-defining items on every scroll event on line 585

* Set number of pizzas to 36 in document.addEventListener('DOMContentLoaded', function() on line 562

* Replace "querySelector" with getElementById on line 564

* Change from document.querySelector to document.getElementById in variable windowwidth inside of function determineDx on line 429

* Set variable phase outside the for loop on line 537 to prevent it from being created during each iteration

* Set variable elem outside the loop on line 564 to prevent it being created each iteration

* Move variable movingPizzas outside the for loop to prevent a DOM call during each loop

* Use a transform on line 572 instead of window.items[i].style.left = items[i].basicLeft + 100 * phase + 'px';

* Calculate number of pizzas based on window size

#### Computational Efficiency:
Time to resize pizzas is less than 5 ms using the pizza size slider on the views/pizza.html page. Resize time is shown in the browser developer tools.

* Move document.querySelectorAll(".randomPizzaContainer") outside of the for loop

* Change to use a switch to set width of pizzas to eliminate Forced Synchronous Layout and eliminate using the function determineDx for pizza widths

* Replace document.querySelectorAll with document.getElementsByClassName

* Move randomPizzas.length to a local variable so that the length of the array doesn't have to be accessed during each loop

