## Discovery

<!-- .element: class="fragment" --><img src="resources/images/testing/justice_loaded.png">

Note:

I built a simple javascript performance toolbar (called Justice.js) for what I call "Performance Discovery". It loads on our sites for our loggged in product team members.

With synthetic testing, we are only testing a tiny number of pages and not that many people are looking at that data.

With RUM testing, we test a whole lot of pages but those stats are averages which aren't always helpful.

So the goal with the toolbar was to expose problematic pages which may be something we should either start monitoring OR if there's a one off issue - report it so it can be fixed in the short term.

Since it has a FPS meter built in - it's particularly good at exposing clunky scroll events on pages with parallax effects or maybe an ad that's being particularly naughty. 

If nothing else, Justice has been pretty good at raising performance awareness. To just get more people thinking about performance.