## GIT annotation

Note:

Each production deploy kicks off a round of synthetic testing on our production sites and those tests get tied back to a specific GIT hash so we can quickly correlate code changes to perf changes.

That way we can verify perf stats are roughly what we thought they'd be for that deploy.

And it helps to identify regressions
* sometimes some work may accidentially get undone
* sometimes a new bottleneck is introduced
* in all cases, we want to tie that to a code change if possible

** PRO TIP: After a deploy, the server response time is often slower than normal. Caches might be empty and some deploys take longer than others (big data migration for example). Those abnormalities can distort test results. But we don't want to spend time analyzing a problem when their actually isn't one.

So right after a deploy has "finished" we fire a background job. That job then polls a Graphite instance until our 90th percentile "server response time" stat returns to levels similar to what they were before the deploy. That all depends on your stack but I've found that this helps to reduce the noise. If you have really flat deploy recovery times, a simple delay might work for you. For us, we needed to go a step further.