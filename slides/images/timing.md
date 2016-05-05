## Timing  

* <!-- .element: class="fragment" --> Load critical images first
* <!-- .element: class="fragment" --> Delay secondary images
* <!-- .element: class="fragment" --> Preloader


Note: For the "critical" images (heroes, etc), leverage the preloader to have them be loaded first. Use the most direct method to obtain those images (e.g. `<picture>` element). They are not blocking, but still VERY important to the users— and very important to editorial teams as well.

For any secondary images, load them only when you need them. Save network connections and user's bandwidth / battery power. For these, lazy-loading techniques are usually best.

Loading everything immediately can cause network bottlenecks on the client, and not leveraging the preloader will cause content to show up much later. Your image requests will be "fighting" for tcp sockets, particularly true if you load ads which load all kinds of assets from many domains.
