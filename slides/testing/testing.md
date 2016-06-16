## Performance Testing and Tracking


Note:

For Testing and tracking, we've focused mostly on synthetic tests thus far.
  
The level of detail provided by synthetic testing is high, which is helpful for analysis. One my favorite features are video recordings which are really helpful to get the feel of the load cycle of a web page. And a before/after GIF is super easy to grok thing - for anyone you want to share results with.



Controlling the conditions for how a page is loaded is particularly important to us since our pages are complex.
* Based on visitor stats, we emulate the most popular browsers and devices for our particular audience.
* For networking, we emulate conditions based on national averages for those browser/device combos.

Since every page load with ads is a unique flower, it's very helpful to be able to remove variables when we are dabbling at optimizing one specific, non-ad related thing. So we test and track our pages both with and without third party things - like ads and trackers.

We test drove a few SAAS performance metric providers but ended up going with ...
* Speedcurve for production
* And a private Webpagetest cluster for staging
	* We do a lot of testing, far more than what the public Webpagetest.org API limits would allow. With the exception of sandboxing permissions, setting up a WPT is realtively easy.

** For both production and sandbox environments, the thing that's actually gathering the metrics is Webpagetest - Speedcurve uses that as it's backend. Which is ideal since we already know how to use it and we don't have to do any re-interpretation of results due to differences in testing methodologies. Something that used Selenium for example might give different results and have different constraints. We just avoid that complexity by using a single backend that we know and trust.