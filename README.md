# Website Performance Optimization portfolio project

The purpose of this project was to optimize the performances of two basic pages:

* index.html 
* views/pizza.html

Note: to run the project, clone the repository and open ``/index.html`` and ``/views/index.html`` in a browser. 
###Part 1: Optimize PageSpeed Insights score for index.html
To do this, I replaced the CSS links to style.css and googleapis(for font) with style tags in the &le head &ge element.
I also added `media="print"` tag to css link to print.css to prevent it from being downloaded by browser. 
To prevent unneccessary java script from blocking the render of the page, I moved the script blocks to the end of body.  
Finally, I edited two images in the page: profilepic.jpg and pizza.jpg.  After resizing the images to smaller sizes, I conpressed them and saved them as png.  Doing this reduced the sizes of images significantly and helped the browser load the page faster. 

###Part 2: Optimize Frames per Second in pizza.html
#### FPS when scrolling:
The FPS in pizza.html was low because the browser would repaint the whole page everytime the background pizzas moved.  I solved this problem by adding the css property `will-change: transform` to the background pizzas.  This eliminated all of the painting, making scrolling seamless. 
#### Reload time after changing the size of pizzas:
moving the slider to change the size of pizzas would cause mutiple forced synchronous layout calculations.  This significantly slowed down the repaint of pizzas.  I changed the `changePizzaSizes()` function to only force one synchronous layout calculation and use that result for all pizzas on the page.  This reduced the repaint time to below 5ms. 