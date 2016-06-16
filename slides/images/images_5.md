## Formats


Note:

Opinions on image formats can be incredibly dogmatic. People love a good image format war - and it can be difficult to sift through all the information and choose what formats you want to support.

I've looked at:
* FLIF
* BPG
* JPEG 2000
* JPEG XR
* WEBP
* JPEG (many encoders)
* PNG (a few encoders)

* While I don't claim any codec is superior or inferior to the other, all things considered including ease of implementation, our stack (and my suggestion) as of today:
  * JPEG
  * PNG
  * WEBP
  * GIF 
    * recent autoplaying inline video support on Safari iOS will *probably* change this recommend soon to MP4/WEBM videos
      * previously, autoplay would always full screen