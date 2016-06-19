### Development Asset budget testing

<img src="resources/images/testing/lightbike.png">

Note:

- prevent chubby production deploys

- runs locally, your browser
- simple budget stats
- only one who uses
- new front end is lean

We also use a thing called LightBike which I also wrote, that just validates a project complies with our new static asset budges (fonts/CSS/etc). That can be run locally and just uses your browser to gather stats via HAR. The important part is LOCAL and SIMPLE STATS - so that just about anyone can use it. It's sort of clumsy/ugly but it does the job. That's been helpful as we build out our new front end which will eventually power all our sites. Needs some more work : )