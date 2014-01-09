--- 
layout: post
title: Parsing Google Voice Data with Symfony.
---



* For the past few months I have wanted an excuse to write some [PHPUnit](http://phpunit.de/) tests. They're so much purer than Drupal simpletests that I write more often.
* I've wanted to get my hands dirty in [Symfony.](http://symfony.com/) It's inevitable for a Drupal Developer.
* I wanted to do some data visualization. I follow a lot of journo/hacker community on Twitter.
* And I wanted to know if I am actually using exclamation points more frequently than in years past (Spoiler alert: I am!). Doesn't everyone want to know that?

Those desires came together recently one a person project to graph my exclamation point usage in Google Voice texts. (@todo, add link to blog post). It was fun to work and I am now looking for feedback on what to do next with this code. I've got a few competing ideas.

I'll start on the front end and work my way backward.

### jqPlot and data presentation.

[jqPlot](http://www.jqplot.com/) as a javascript library handled the data I had pretty well. Aside from an unexpected timezone eccentricity/possible bug (Add link) I was extremely pleased with the jqplot itself.
The downside for me was working through an abstraction layer.
I used jqPlot simply because they're was a Symfony bundle that made it super easy to take some PHP variables and make a working line chart. Customizing is always the hard part with server-side libraries that configure client side libraries.
As a Drupal developer I have seen this dynamic play out with jQuery Cycle, Google Maps, Flexslider and others.

As I said, in any of those server-side/client-side pairs, the server-side library makes getting up and running really easy.
Customizing though generally requires first looking up in the client-side library what options are available, figuring out how to make the change client side; and then figuring out what server side change will generate the desired client side change. And it feels like too many hoops to jump through when one simply wants to change the format of a label.
In fact at my job at Palantir we generally just skip the integration module for widgets like flexslider.
Instead we'll generate the markup we want and directly implement the appropriate Javascript calls in a small custom js file.
We find it faster and more maintainable than adding yet another contrib module to a project. 

### Where should the analysis happen?

In my exclamation point analysis I took a giant php array of messages and looped over them to check for
<pre>if (strpos($message['message'], $string_to_find) !== FALSE) {
  $results[$month]['hits']++;
}</pre>

PHP works for simple string search. And it can do more advanced analysis. But the friction would increase. To the data analysis pros out there, is PHP a non-starter the the analysis step? Would I be better off if [R](http://www.r-project.org/) or some other statistical tool performed this step and handed the results back to PHP or javascript for presentation? Or maybe go a step further and R should be generating the visualization too?

### What should the Symfony organization be?

Currently I have an entire Symfony App version controlled and available. That's probably overkill. If GoogleVoiceParser is going to live on in the PHP world (and I don't know if it will) I think it should be two packages. One package would be a Symfony bundle that would provide Controllers and default routing and services definitions (xml or yml) and whatever other boilerplate is necessary to make the bundle work. Ideally this package would be as thin as possible because, this kind of analy The second package would contain standalone classes that become the services.


