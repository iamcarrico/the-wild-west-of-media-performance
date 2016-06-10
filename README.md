The Wild West of Media Performance: A Vox Story
===============================================

A full version of these slides can be found at [https://iamcarrico.github.io/the-wild-west-of-media-performance/](https://iamcarrico.github.io/the-wild-west-of-media-performance/).


## Running locally

Be sure to install all of the npm packages that are being used by running `npm install`. This will also download any bower packages that are in use.

To run the presentation, use `npm start`— which will create a server running on port 9000 (and automatically open a window). Full instruction to use the slides can be found on the [Reveal.js documentation](http://lab.hakim.se/reveal-js/).




Sections:
  Images
  Fonts
  Ads
  Testing
  














The Wild West of Media Performance: A Vox Story


Proposed changes to the flow of the presentation:

  Images:

    1. Timing (helps to determine later things)
      - Load critical images first [in our case that means lede images for articles and "heros" for group pages like the homepage]
      - Delayed load everything else [for us, that's images in the article body ... sidebar things ... "related content" type modules, etc. Basically everything not a lede/hero)

    2. Delivery (first thing [timing] restricts some choices)
      - Boring old hardcode image tags: rare, but used for some one off sites and some logos
        - these rare cases are becoming rarer and don't really need much rethinking
      - Lazy-loading / Javascript responsive images
        - img tag and block element background attributes
      - Picture element (srcset + mime + responsive)
        - well suited for critical images (lede/hero) because they can leverage the preloader aka look ahead parser
        - starts downloading image as soon as html is parsed
        - we previously used lots of lazy-loading but we are continuing to roll out more and more picture els ... this has some front end / design hurdles to consider so it takes some time

      [*] We use all 3

    3. Processing
      - Pre Processing
        - with some small exception, we don't use preprocessing as it's hugely inefficient for the scale of what we do with images
        - could work for others
        - advantage would be "slow" (> 1second) processing time might be acceptable so you could really get crazy with brute force style image compressors
      - Real time
        - SAAS options
          + just works
          - $$ and control
        - Open source (*)
          + $$, control, image nerd heaven (I can run amuk)
          - a lot of work to maintain (especially scaling and upgrading)

      [*] We opted for an open source solution called Thumbor. It's amazing and I highly recommend it. The team at Globo.com who created and supports it are a great group of really nice people.

      4. Formats
        - Welcome to hell. The dogma is thick and murky. It's a rabbit hole
        - My suggestion: PNG/JPEG/Webp and GIF for animated ... if you must, skip jpeg2000,  jpegxr and everything else
        - See me after the show for a nerd battle
        - Our experience with Webp has been largely positive made for big easy wins










Rando Notes:

    ** Halarious gotchas to watch out for when using real time image processing + responsive images is high DPI devices where GIF's are used. You want to make sure to NEVER upscale images via the image processor. If you need to upscale to fill a space, use CSS. I've seen GIF's which had a source file size of 250kb but got upscaled by the image processor which resulted in a (still crappy looking, zero value) 50MB gif. That's brutal, especially for an iPad on 4G or less.

    ** Tips and tricks
      - Preconnect!
        - If you know what endpoints your webpage will be using (even just the ones you know for sure) go ahead and throw some preconnect meta tags up there.
        - Downside, no Safari OSx/iOS or IE : (
        - Upside, non-trivial increase in page performance (at least in our case)
      - dns-prefetch ... maybe
        - In our case, using the same list of domains as preconnect we saw no measurable impact ... all values fluctuated within standard deviation
        - Probably doesn't hurt but we opted "no" given the lack of supporting data via my experiments. Your mileage may vary, try it, test it.

    ** What is a performance engineer?
      - As a performance engineer I am:
        - A student: I read ... a lot. Books, blogs, specs, src ... all the thigns. I mess with things. What if I did this?
        - A scientist: I must be able to quantify my work, before/after. Therefore, I perform a LOT of experiments. I use many tools. Webpage test is at the top.
        - A detective: If anyone on the team notices a performance bottleneck symptom, it's part of my job to dive in an investigate what is causing the issue and often propose a solution.
        - A steward: It's quite common that I need to work cross team, often putting members of one team in touch with another -
        - A programmer: Sometimes I get to write code. It's the best. My favorite thing to build is tooling but I do implement changes as well.
          - Justice
          - Lightbike
          - Tempo
        - Back seat Ops driver: I make annoying requests to the Ops team and occasionaly get to throw a wrench into their perfectly tuned systems. Ops team loves me : )


Very high level ideas:
  - GIF's where possible (before/after)
    - Webp
    - Picture
    - Font's




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

      - Formats:
        - We have very high Chrome usage (on desktop, and a good amount on mobile) so we used webp
        - Thumbor
          - Already using for cropping
          - Enabled webp
          - client side detection for explicit webp
          - server side detection for implicit webp, to help fill the gaps on old codebase including older images
            - via accepts header
            - caching layers caused problems with special headers
          - Webp deployed (gif of load times)

      - PROBS:
        - Media company know for their high quality content and brands, compression artifacts are not tolerated.
          - deep, deep rabbit hole into image compression and what makes a compressed image "bad"?
          - SSIM
          - DSSIM
          - Internal small sample experiments, huge deviation on quality perception

      - Load order:
        - We love images. Big ones and lots of them.
        - Don't lazy load the lede image
          - Critical Image, load this as soon as possible.
          - Picture element
            - responsive size
            - multi format

    - Data collection, per deploy
      - higher than average server response times seen right after deploy
        - Solution: use Splunk logs to analyze perc 90 response times, THEN fire off SpeedCurve tests

    - Constant battle:
      - Innovative media startup is, well always innovating == vendors/assets are constantly changing
      - Video team could change, Revenue (ads) team could change, too big to track all changes.
      - What "things" are our and what things are not ours?
        - We have to track both
          - over time, we accumulate more third party things
          - ad assets change origins very quickly
          - this is hard, because Webpagetest can only block explicitly where what we need to so block by default and allow explicitly. Unsolved problem.




    - Fonts: (fix FOIT zomg before presentation)




## Slide Template

These slides were made with [Reveal.js](http://lab.hakim.se/reveal-js/) with my own template, found here: https://github.com/iamcarrico/slides-template

## License

This content within the presentation is licensed under the Creative Commons Attribution-ShareAlike 4.0 International ([CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/)). All code is licensed under the [MIT License](https://github.com/iamcarrico/the-wild-west-of-media-performance/blob/master/LICENSE.md)
