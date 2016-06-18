# RUM

Note:

	 We were already capturing basic metrics via Google Analytics. Great freebie!

      :: Ads change on every page load ::
      - Each time you load a page with ads you will get different results ... because the contents have changed. Often drastically.
        * If the content of a page is effectively random, it's very difficult/impossible to get meaningful insight into what the effect of the latest performance improvement is.

      :: Content varies wildly ::  
      - Content differs wildly even for the same page type
        * Even if we lumped RUM data into page *type* silos, one article maybe have 800kb of content and another may have 2MB. I don't like saying those words out loud but that is the reality of working on a media site.
        * Since we're talking about 100k-1M page loads ... and we get averages, the data is not very satisfying.
      
      :: Transient Popularity ::
      - Being a media org, our article pages popularity are transient in nature
        * Which means we can't get meaningful data over time for our articles.
        * If nobody is loading the pages, the data isn't being collected.
        * We don't really know how our perf work is affecting page load times using RUM since those pages often aren't being visited any more.

      ** There is nothing wrong with RUM. But If we did want to leverage RUM stats more heavily, it's clear that we'd need to put in significant effort. One day, we will. But in the beginning, we wanted to move fast and make some meaningful changes and RUM wasn't the answer.