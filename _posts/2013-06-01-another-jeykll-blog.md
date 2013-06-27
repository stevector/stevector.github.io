--- 
layout: post
title: Another Jekyll blog
main-image: "all_the_things.jpg"
image-attributes:

---


I'm jumping on the bandwagon. My vague ambitions to start a blog have combined with my desire to built something outside of [Drupal](https://drupal.org) (the technology that has been at the center of my job for six years). So like [The state of Hawaii](http://portal.ehawaii.gov/page/developers/), [The federal government](http://developmentseed.org/blog/new-healthcare-gov-is-open-and-cms-free/) and Drupal developers  [Jeff Eaton](http://angrylittletree.com/), and [Matt Farina](http://engineeredweb.com/blog/why-switched-to-jekyll/) I've turned to Jekyll.

From [the Jekyll docs page](http://jekyllrb.com/docs/home/):

> Jekyll is a simple, blog-aware, static site generator. It takes a template directory containing raw text files in various formats, runs it through Markdown (or Textile) and Liquid converters, and spits out a complete, ready-to-publish static website suitable for serving with your favorite web server.

That's a lot of jargon that boils to two principles that appeal to me.

### 1. Only think about something when you have to think about.
For a webpage like this to get to a browser it is necessary for a computer to stitch together these words along with some template code and stylesheets. Jekyll does that work as I write and save a post. Drupal and most other modern site-building tools will do that work over and over again as more people as for the webpage. The "over and over again" approach allows a site to be slightly different for each logged in user or to constantly update something like the "most popular stories" list. Losing the ability to "think" every time a page is requested feels like I've thrown out the majority of my toolbox as a web developer. And that's ok. For a site this simple it's not necessary to carry around those heavy tools.

### 2. Version controlling content
Jekyll keeps the contents of the posts in text files (Markdown in most cases, mine included). That means the same tool (Almost certainly [git](http://git-scm.com/)) used for managing changes to the code of the web site can be used for tracking changes to the contents. And the tools for managing code have gotten amazing in the past few years. [Clay Shirky's TED talk on git](http://www.ted.com/talks/clay_shirky_how_the_internet_will_one_day_transform_government.html) is the best explanation I've seen of why git is worth noticing. For one thing, controlling content through git means that a person can [fix a typo in someone else's blog](https://github.com/eaton/eaton.github.com/commit/fd2b2b5ab42296cb803c6fca19e944ab60a061bc) as easily as they'd correct a bug in open source code. Managing content with git will produce other unexpected modes of collaborating and I'm exciting to have a blog that can be a part of this shift.






