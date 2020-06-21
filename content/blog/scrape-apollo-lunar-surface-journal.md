---
title: "Scrape The Apollo Lunar Surface Journal image library"
date: 2020-06-20T18:36:37+02:00
draft: false
---


Last year I went to a light festival organized to celeberate Apollo's 50th Anniversary. It was supposed to project Saturn V on a tower and simulate the historical launch. Unfortunately that evening I chose a wrong angle to watch the show and missed most of interesting parts. 

Few weeks later I decided to go through NASA's website to see more high quality images, and I found a real [treasure](https://www.hq.nasa.gov/alsj/):


> The Apollo Lunar Surface Journal is a record of the lunar surface operations conducted by the six pairs of astronauts who landed on the Moon from 1969 through 1972. The Journal is intended as a resource for anyone wanting to know what happened during the missions and why. It includes a corrected transcript of all recorded conversations between the lunar surface crews and Houston. The Journal also contains extensive, interwoven commentary by the Editor and by ten of the twelve moonwalking astronauts.


This Journal contains so many images but it's a bit hard to navigate through them. So I decided to write a simple scraper to fetch images for each Apollo mission easily from CLI, it was also a great oppurtunity to explore scrapers written in Go.

After a quick research I found [Colly](https://github.com/gocolly/colly) which seems quite easy to use with nice and clean API. You can find the source code of the script [here](http://github.com/goolila/apollo-images). It creates a worker pool (1 worker for each CPU) and then puts image links on a queue which is consumed by our workers. Here's how it looks like when you run it:

```
$ ./apollo-images -mission 12 -sleep 1000
🚀 It was so much fun: https://en.wikipedia.org/wiki/Apollo_12
Visiting https://www.hq.nasa.gov/alsj/a12/images12.html
[worker 1] downloading  https://www.hq.nasa.gov/alsj/a12/ap12-S69-57076HR.jpg to /tmp/apollo-images/12/ap12-S69-57076HR.jpg
[worker 0] downloading  https://www.hq.nasa.gov/alsj/a12/a12-lam7HR.jpg to /tmp/apollo-images/12/a12-lam7HR.jpg
[worker 2] downloading  https://www.hq.nasa.gov/alsj/a12/a12-lse76gHRsite4actual.jpg to /tmp/apollo-images/12/a12-lse76gHRsite4actual.jpg
[worker 3] downloading  https://www.hq.nasa.gov/alsj/a12/a12-lse730HR.jpg to /tmp/apollo-images/12/a12-lse730HR.jpg
```

I highly suggest using a fair amount of sleep time between requests just to not hammering on the server and use the journal in a responsible way.

Most of the photos are breath taking and so simple at the same time. These 3 images are the most amazing ones for me so far:


[![1](/img/blog/scrape-apollo-lunar-surface-journal/a11pan1105549HR.jpg#tunecover)](/img/blog/scrape-apollo-lunar-surface-journal/a11pan1105549HR.jpg)

Neil took this pan from a spot southeast of the LM while Buzz's was removing equipment from the SEQ Bay. *

[![2](/img/blog/scrape-apollo-lunar-surface-journal/AS11-44-6586HR.jpg#tunecover)](/img/blog/scrape-apollo-lunar-surface-journal/AS11-44-6586HR.jpg)

View of the front of the LM.

[![3](/img/blog/scrape-apollo-lunar-surface-journal/AS11-36-5334.jpg#tunecover)](/img/blog/scrape-apollo-lunar-surface-journal/AS11-36-5334.jpg)

Earth view. 

I hope you visit the library and enjoy it as much as me.

**Photo credit for all images goes to NASA/ALSJ.**