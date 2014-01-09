--- 
layout: post
og_image: "exclamation_point_usage_graph.jpg"
title: I graphed my skyrocketing exclamation point usage!
---


### WHAT is the deal?

I parsed over four years of my Google Voice data to look for exclamation points in my sent messages. This graph shows what I found.

### WHY did I do that?

My girlfriend and I had talked about how nearly all of our messages contain exclamation points.
I had chatted with friends about exclamation points’ omnipresence.
And then [Ben Crair](https://twitter.com/bencrair) wrote [a story in The New Republic](http://www.newrepublic.com/article/115726/period-our-simplest-punctuation-mark-has-become-sign-anger) that brought some more high profile ancedata about exclamation points as “sincerity markers.”

After all that converation I figured that this question was entirely answerable.
So I downloaded my full Google Voice history and parsed it.

### WHO was I texting?

Mostly my girlfriend. We've been together since late October of 2012.
I suspect her frequent exclamation usage has influenced me.
Maybe I'll refactor my code a little to separate out the percentage of text to her that get exclamation points as compared to everybody else.

### What does it matter?

The English language has a defacto standard of being controlled by its users.
Unlike French, which is controlled by a central authority, English is driven by ordinary people.
And dictionary and style guide publishers are agree to grab free publicity by annoucing which new works they've recognized in a given year.
The ease with which lingustic trends can now be identified will only speed up this process.
Sure [dictionary xyz] recognized in 2013 that literally stopped meaning literally and soon will we literally be able to pin point when a meaning shifts.
And for the editor who wants to rewrite the textbook meaning of exclamation points, the evidence is mounting.

### How did I do that?

First, I [exported my Google Voice history with Google Takeout](http://techcrunch.com/2011/09/06/google-now-lets-you-export-google-voice-data/).
Then I wrote a couple of PHP classes to parse the files in arrays that could be manipulated more easily.
Those classes then went into a [Symfony](http://symfony.com/) bundle that used [Altamira](https://github.com/Malwarebytes/Altamira) to display the data through [jqPlot](http://www.jqplot.com/).
I've got [an open Pull Request against my blog](https://github.com/stevector/stevector.github.io/pull/9) with an in-progress post that has more details on how the code works.
This code was the first time I wrote a Symfony bundle or app and it shows.
There's plenty of refactoring to be done.
Pull requests welcome.

### WHERE can the work be checked?

Well I don't like the NSA reading my texts and I don’t want you reading them either.
So to a certain extent you’ll just have to trust me.
Jump into a conversation with me in the comments of this post or in the pull request for the upcoming blog post if you have ideas for how such data could be shared in a sanitized fashion.
