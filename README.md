The Wild West of Media Performance: A Vox Story
===============================================

Main touch points:
  - Realization: TheVerge used for "what not to do" examples on perf conferences
  - A team was formed (team assemble!!!)
  - Data collection and historical performance tracking
    - Define and measure the problem.
    - Historical data to track progression/regressions.
    - Still need better notifications
      - complicated by dynamic page content, per page load (:knife:)

  - High impact changes

    - Images:
      - We have very high Chrome usage (on desktop) so we used webp
      - Thumbor
        - Already using for cropping
        - Enabled webp
        - client side detection for explicit webp
        - server side detection for implicit webp, to help fill the gaps on old codebase including older images
          - via accepts header
          - caching layers caused problems with special headers
        - Webp deployed (gif of load times)

    - PROBS:
      - Media company know for their high quality content and brands, compression artifacts are not tolereated.
        - deep, deep rabbit hole into image compression and what makes a compressed image "bad"?
        - SSIM
        - DSSIM
        - Internal small sample experiments, huge deviation on quality perception


    - Fonts: (fix FOIT zomg before presentation)




## Slide Template

These slides were made with [Reveal.js](http://lab.hakim.se/reveal-js/) with my own template, found here: https://github.com/iamcarrico/slides-template

## License

This content within the presentation is licensed under the Creative Commons Attribution-ShareAlike 4.0 International ([CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/)).
