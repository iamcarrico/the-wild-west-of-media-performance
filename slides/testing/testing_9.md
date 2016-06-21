## Performance Discovery

<img src="resources/images/testing/justice_loaded.png">

Note:

- not monitoring every page
- perf toolbar: Justice.js
- raise awareness & find things to monitor/fix
- basic metrics with color coded budgets
- FPS meter, catalyst for scrolling issues



We also use something I wrote called Justice.js, which is a performance toolbar that provides user timing stats and a steaming frame rate meter. We load that on all of our sites for logged in Product Team members. It's been helpful in raising perf awareness and identifying problems on pages we are aren't monitoring. The FPS meter has been the catalyst for fixing some pages and ads with suboptimal scrolling issues - from parallax things for example.