---
layout: post
title: "The Unbelieveable Beauty of JSON-LD"
modified:
categories: development
excerpt: "Before the release of HTML5, the classic tags that the
search engines had to sift through made it difficult for them to decypher just what content belonged to which part of the page.  Sure
the algorithm eventually got close, but HTML5 put it right on the spot.  If you want to tell the engines what section was the nav bar,"
comments: true
tags: [SEO, JSON-LD, Web Development, schema markup]
image:
  feature:
date: 2015-03-16T06:11:26-05:00
---

## SEMANTICS!

Before the release of HTML5, the classic `<div class="article">`, `<div class="nav">`, or any number of classes or IDs that the
search engines had to sift through made it difficult for them to decypher just what content belonged to which part of the page.  Sure
the algorithm eventually got close, but HTML5 put it right on the spot.  If you want to tell the engines what section was the nav bar, you
wrap it in `<nav>` tags.  The main article content?  `<article>` tags.  Guess what an aside goes in... got your guess?

If you guessed `<aside>` give yourself a cookie!

The engines now have something to directly tell them "The content in here is the article.  This content is a sidebar."  There are
sections, addresses, figures, main areas, and a ton more.  This made SEO a bit easier by helping the engines know just what content
went where and how it related to the rest of the page.  The full [list of HTML tags](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
is available on [Mozilla Developer Network](https://developer.mozilla.org).

The engines were happy that they knew what was what and the world was a better place, however it wasn't enough.  The engines
were hungry for more input.
<figure style="text-align: center;">
  <img id="dog" src="/images/moar_input.jpg" alt="Johnny 5 needs to eat too" style="height: 400px; width: auto;" />
  <figcaption>Need more input!</figcaption>
</figure>

Along comes [schema.org](http://www.schema.org) with their markup.  If someone was named on a page they could use
{% highlight html %}
<div itemscope itemtype="http://schema.org/Person">
  <a itemprop="url" href="https://www.jamesdflynn.com">
    <div itemprop="name">
      <strong>J.D. Flynn</strong>
    </div>
  </a>
  <div itemprop="jobtitle">
    Web Developer, SEO student, All-around nice guy
  </div>
</div>
{% endhighlight %}
and define themselves, along with a number of other entity types as defined on [schema.org](http://www.schema.org).

Google adopted this and started adding schema markup to their knowledge graph, which gave them a new way to link stuff together.  Now
the author of an article or a product on a page could be pulled from the html, added to the knowledge graph, and be found easier, but look
at that markup.  doesn't it seem a little clunky?  Maybe there's a better way to do it?

## JSON to the Rescue!

JSON-LD or JavaScript Object Notation - Linked Data is much easier to read and use than regular markup.  Take the example from above:
{% highlight html %}
<div itemscope itemtype="http://schema.org/Person">
  <a itemprop="url" href="https://www.jamesdflynn.com">
    <div itemprop="name">
      <strong>J.D. Flynn</strong>
    </div>
  </a>
  <div itemprop="jobtitle">
    Web Developer, SEO student, All-around nice guy
  </div>
</div>
{% endhighlight %}

with JSON-LD it can be written as:
{% highlight javascript %}
<script type="application/ld+json">
{
"@context" : "http://schema.org",
  "@type" : "Person",
  "name" : "J.D. Flynn",
  "jobTitle" : "Web Developer, SEO student, All-around nice guy",
  "url" : "https://www.jamesdflynn.com"
}
</script>
{% endhighlight %}

Now take a look at that.  It's cleaner, easier to read, much less clunky, and can be placed in the `<head>` section of your page
independant of the content.  Go ahead and try it out at [Google Structured Data Testing Tool](https://developers.google.com/structured-data/testing-tool/).

Now what are the advantages of one over the other?  To me, one of the biggest advantages is mobility.  I can paste the JSON-LD script
almost anywhere in my page and Google will parse it and use it as intended where the microdata is specific and needs to be exactly where the data is.
There's also the usability.  To me, writing div after div after div can get tedious.  JSON-LD is human-readable and easy to tell exactly what
goes where.

## But Wait, There's More!

It's not just for people or businesses!  JSON-LD and structured data can be used in emails as well with dates and locations of events,
product information, and app integration.  Why does this matter?  Because it matters to Google.

For those of you with Android phones, you may have noticed that Google seems to know you better than you know yourself.  You get reminders
of concert tickets, you get flight status updates, you click on a song and it asks you whether you want to open it on Youtube or your browser.
These are all the result of structured data being pulled and used by Android to make your life easier.

As a web developer, I find this amazing and a little intimidating.  As an SEO beginner, it's exciting.  On my "test" site that I'm attempting to
optimize, I wrote up some JSON-LD and instructed the client to put it on his site.  Now, even though he's not ranking (yet) he is showing
up on the right side of the SERP when searched for directly thanks to a little semantic markup and JSON-LD.

So are you using semantic markup or JSON-LD in your projects, and what difference has it made?  Let me know in the comments.

