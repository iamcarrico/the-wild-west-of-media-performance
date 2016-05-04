## Timing  

Load your "critical" images as soon as possible.
  - leverage the preloader

Delay loading non-critical images until you need them
  - less network contention
  - save users bandwidth


  (https://pbs.twimg.com/tweet_video/CTo0o0dUcAMNJ3w.mp4)
    at what point should you load what images?

- Moving important image requests up the waterfall
  - Image requests are non blocking but
    - they are incredibly important to your users
    - if you don't use the preloader, they will come late
      - loading all images immediately can create a networking bottle neck on the client
      - not leveraging the preloader means important content will show up much later
        - you image requests will be "fighting" for tcp sockets, particularly true if you load ads which load all kinds of assets from many domains
