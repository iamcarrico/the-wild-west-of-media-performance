## Quality Control

Note:

There is a problem with real time processing.

* Quality control

Naive image compression, like JPEG quality=80 does NOT mean you will have images that are 80% as good as the original. That means that even though you have setting of "80%" in your image processing config - the perceived quality to a human may vary greatly. Real time image processing systems need to tackle this issue and trivialize it for the end user of that software.

I am working to solve this issue, for the open source Thumbor project.