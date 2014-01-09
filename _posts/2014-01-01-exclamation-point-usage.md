--- 
layout: post
og_image: "exclamation_point_usage_graph.jpg"
title: I graphed my skyrocketing exclamation point usage!
---


### WHAT is the deal?

I parsed over three years of my Google Voice data to look for exclamation points in my sent messages. This graph shows what I found.

<iframe  src="/assets/post_specific/2014/01/google_voice_exclamation/chart.htm" width="700px" frameborder="0"  height="410px"></iframe>

### WHY did I do that?

My girlfriend and I had talked about how nearly all of our messages contain exclamation points.
I had chatted with friends about exclamation points’ omnipresence.
And then [Ben Crair](https://twitter.com/bencrair) wrote [a story in The New Republic](http://www.newrepublic.com/article/115726/period-our-simplest-punctuation-mark-has-become-sign-anger) that brought some more high profile ancedata about exclamation points as “sincerity markers.”

After all that conversation I figured that this question about how much exclamation usage was increasing could be answered concretely.
So I downloaded my full Google Voice history, parsed it and graphed what I found.

### WHO was I texting?

Mostly my girlfriend. We've been together since late October of 2012.
I suspect her frequent exclamation usage has influenced me.
Maybe I'll refactor my code a little to separate out the percentage of text to her that get exclamation points as compared to everybody else.
I should also note that not every text conversation I have runs through Google Voice.
While the vast majority do, some friends and family still text me directly on my cell number.

### WHAT does it matter?

The English language has a de facto standard of being controlled by its users.
Unlike French, with its [Académie française](http://en.wikipedia.org/wiki/Acad%C3%A9mie_fran%C3%A7aise), English is driven by ordinary people.
[That's not going to change](http://www.economist.com/blogs/johnson/2010/06/english_academy).
In English, dictionary and style guide publishers chase free publicity by announcing newly added words and [words of the year](http://artsbeat.blogs.nytimes.com/2013/11/19/selfie-trumps-twerk-as-oxford-dictionaries-word-of-the-year/?_r=0).
The ease with which linguistic trends can now be identified will only speed up this process.
[In 2013 literally stopped meaning literally](http://www.prdaily.com/Main/Articles/15033.aspx#) and soon will we literally be able to pin point when a meaning shifts.
For the editor who wants to rewrite the textbook meaning of exclamation points, the evidence is mounting.

### HOW did I do that?

First, I [exported my Google Voice history with Google Takeout](http://techcrunch.com/2011/09/06/google-now-lets-you-export-google-voice-data/).
Then I wrote a couple of PHP classes to parse the files in arrays that could be manipulated more easily.
Those classes then went into a [Symfony](http://symfony.com/) bundle that used [Altamira](https://github.com/Malwarebytes/Altamira) to display the data through [jqPlot](http://www.jqplot.com/).
I've got [an open pull request against my blog](https://github.com/stevector/stevector.github.io/pull/9) with an in-progress post that has more details on how the code works.
This code was the first time I wrote a Symfony bundle or app and it shows.
There's plenty of refactoring to be done.
Pull requests welcome.

### WHERE can the work be checked?

Well, I don't like the NSA reading my texts and I don’t want you reading them either.
So to a certain extent you’ll just have to trust me.
Jump into a conversation with me in the comments of this post or in the pull request for the upcoming blog post if you have ideas for how such data could be shared in a sanitized fashion.
