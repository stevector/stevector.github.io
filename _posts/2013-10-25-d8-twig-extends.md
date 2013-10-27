--- 
layout: post
title: Make your Drupal 8 theme easier to maintain with this one weird trick (Twig's "extends" concept)
---

### WHAT is Twig's "extends" concept

Drupal 8 has a new templating system called [Twig](http://twig.sensiolabs.org/) that comes from the [Symfony](http://symfony.com/) world.
I recommend learning about Twig and Drupal 8's use of it by watching a video of one of the many recent conference presentations on the topic like [this one from Drupalcon Portland](https://portland2013.drupal.org/session/using-twig-new-template-engine-drupal-8).
Twig contains within it a different model for overriding templates that can be used in combination with Drupal's traditional naming-based template overrides.
[Read Twig's own documentation of 'extends' here.](http://twig.sensiolabs.org/doc/tags/extends.html)

### WHY is it helpful

Last weekend when I was working on a personal Drupal project ([nerdologues.com](http://nerdologues.com)) and ran into a common theme development pain point.
I wanted to print some fields in the header tag of my node template for only one node type.
In Drupal 7 (and prior versions) this process involves making a a complete copy of the `node.tpl.php` file ([See the drupal.org documentation of this process here](https://drupal.org/node/17565)).

Copying every line of node.tpl.php to node--article.tpl.php only to change a few lines makes the theme of a given drupal site extremely WET ([Write Everything Twice](http://en.wikipedia.org/wiki/Don't_repeat_yourself#DRY_vs_WET_solutions)).
What if instead of duplicating the entire node template file to a node-type specific name, I could make that node-type specific file contain only the overrides?

That's what Twig 'extends' concept does!

### HOW is it used

Here's an example `node--article.twig.html` that moves field_image into the header tag of the node.

<pre>
{% extends "themes/sub_bartik/templates/node.html.twig" %}

{# Override the header_fields block to put field_image there because this site
   needs it there. #}
{% block header_fields %}
  {{ content.field_image }}
{% endblock %}

{# Override the content block to hide the field_image subvariable because
   it is being rendered in header_fields. #}
{% block content %}
  {% hide(content.field_image) %}
  {{ content }}
{% endblock %}
</pre>

That is all that is needed!

Compare that to the amount of code in the parent template being overridden. LINK NEEDED.

To make this kind of overriding possible, the parent template needs to declare which sections can be overridden. In this example I've declared two "blocks" (in Twig-speak, the Drupal community might start calling these "codeblocks" to reduce confusion with Drupal core's Block module) that designates which pieces of the template can replace.

Heres one addition to node.twig.html in a copy Bartik's version:

<pre>
    {# This empty block allows child templates to insert markup into this
       place in the header without re-writing the entire template. #}
    {% block header_fields %}
    {% endblock %}
</pre>

Addition two in node.twig.html
<pre>
    {# By wrapping the content variables in a block, this template allows child
       templates to insert markup into this spot without re-writing the entire
       template. #}
    {% block content %}
      {{ content }}
    {% endblock %}
</pre>

### WHERE does this code go

You can see the the complete example code which is a sub-theme of Bartik here [in an alternate branch of the github repo of this blog you're reading](https://github.com/stevector/stevector.github.io/tree/twig-extends-example).
To test it, git clone that branch into /themes of a Drupal 8 site and enable  Notice that again that the "parent" node.twig.html is in this sub-theme.
By having a node.twig.html in the subtheme, Drupal (and Twig) completely ignore the node.twig.html in Bartik and node module.
That kind of overriding where a template file in the theme completely supersedes Core is the same as previous versions of Drupal.

### WHO should write these "blocks"

This example is illustrates how 'extends' can be used a site owner in a **site-specific theme**.
I have shown this code around at [BADCamp](http://2013.badcamp.net/) this weekend and the reaction from [Carl Wiedemann](https://twitter.com/c4rl) and others has mainly been something like "Drupal Core shouldn't put these blocks in templates yet (or maybe ever) because we don't have enough experience with them."
I agree.
Drupal has a pattern of proving concepts in the contrib space and then moving those concepts into core.
And even before making a contrib base theme using Twig blocks, someone has to use them on a real site.

### When 

Heavy use of the 'extends' concept in Twig will start when developers start building Drupal 8 sites and adding site-specific themes.
