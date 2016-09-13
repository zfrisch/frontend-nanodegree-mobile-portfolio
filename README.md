# Website Optimization
This Project is For Udacity Coursework [Udacity Front-End Project](https://github.com/udacity/)

## Instructions For Use
* Download this Project or clone repository through Git.
* Open Index.html in a Web Browser

## Optimizations for pizza.html, main.js, and style.css
* minified JS/CSS/html using:
    * https://jscompress.com/ 
    * https://cssminifier.com/
    * http://www.willpeavy.com/minifier/
* added will-change property to .mover class

* resizePizzas()
	  * changed out pizzaSize DOM searches for a reference
	 
* changePizzaSizes(), sizeSwitcher()
    * made a reference to randomPizzaContainer and utilized that instead of querying the DOM every time.
    * added global variables for windowWidth, element offset width, and element offset width divided by windowWidth, instead of having them computed in for loop.
    * removed determinDX function as it was rather pointless. Hardcoded the basic math into the for loop and made the sizeSwitcher globally accessible for quick use. This removes a function call and lowers are speed.

* UpdatePositions()
    * pulled document.body reference and calculation out of for loop and used window.scrollY / 1250 as const
    * changed querySelectorAll to getElementsByClassName
    * made phase for sin wave an array to do 5 calculations once and then reference in for loop.
    * changed style.left to style.transform 

* scroll event listener
    * originally found snippet on html5 rocks
    * we are using this to make sure the updatePositions function isn't firing unnecessarily.
```
var last_known_scroll_position = 0;
var ticking = false;

window.addEventListener('scroll', function(e) {
  last_known_scroll_position = window.scrollY;
  if (!ticking) {
    window.requestAnimationFrame(function() {
      updatePositions();
      ticking = false;
    });
  }
  ticking = true;
});
```

* DOM Content Loaded
    * reduced pizzas from 200 to 35
    * changed querySelector to getelementbyid and pulled out of for loop as const
    * had to set the original left position of each element so that translateX could be used effectively in the updatePositions function

# Index.html 
* used web font loader
  * This prevents the font from Google from blocking page rendering
* Changed GA script tag to defer and placed script utilizing GA at end of page
* Made all CSS Inline
* Optimized all images
  * used ImageMagick to reformat all images to lossless webp
