<video  autoplay loop>
	<source src="lib/picture_element.mp4" type="video/mp4" />
</video>


Note:

If you want to load some images a bit later, then can do that with javascript.

* Reduces client resource contention (network & CPU) 
* Saves the user bandwidth
* Saves us $$ on CDN costs

** We use all three methods of loading images, depending on the image placement. 

In the future, we'll be using the <Picture> element more and more.

If client hints gets enough browser support, I'd love to use that to simplify the <Picture> element markup.