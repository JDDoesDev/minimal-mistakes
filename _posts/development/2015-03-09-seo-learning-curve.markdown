---
layout: post
title: "The Steep Learning Curve of SEO"
modified:
comments: true
categories: development
excerpt: "If you read my last post on web development then you'd know that I am an SEO convert and
wanting to learn everything that I can about it, but like most things worth learning, there are literally thousands
of places that I could start.  So where do I start?  Should I read the copy of SEO for Dummies that came with the workshop I went to,
or should I just read every blog on Moz or Search Engine Land, should I try to emulate everything I saw at Search Marketing"
tags: [learning seo, website development, search engine, schema markup]
image:
  feature:
date: 2015-03-09T17:17:12-05:00
---

## Where to Start?

If you read my last [post on web development](/development/developer-search-engine-den/) then you'd know that I am an SEO convert and
wanting to learn everything that I can about it, but like most things worth learning, there are literally thousands
of places that I could start.  So where do I start?  Should I read the copy of SEO for Dummies that came with the workshop I went to,
or should I just read every blog on Moz or Search Engine Land, should I try to emulate everything I saw at Search Marketing
Expo.  What's the best method?

I'm sure that this is one of those questions that has no right answer.  If I asked 5 people I would probably get 25 answers, and
that's alright.  There's more than one way to do SEO and there are many places to start.  I've decided to start by just jumping into
it.  I have 2 pages that I'm going to be working with, including this one.  I've set up Google Analytics accounts on all both and I'm
generating reports for a baseline to see if what I am doing is having any effect.  I have also decided to to try learning SEO by
using several methods including link building, keyword optimization, and schema markup where appropriate.

## Madness to My Method

So my new, personal site is going to be a sort of sandbox for learning SEO.  This is where I can play with different tactics and strategies
as well as seeing how rankings fluctuate based on content, links, and other factors.  I've also taken on an SEO client, although
they are kind of an experiment as well.  My goal is to follow the Hippocratic Oath and first do no harm or more simply put, not be evil.

Thus far I've combed through his code (developer powers activate!) and found a few things that could be improved.  For starters,
he didn't have a sitemap which was my most immediate concern.  Secondly, the `<title>` tags weren't nearly as descriptive as they could
be.  Third, there was no `<meta type='keyword'>` tag which, in my opinion, is much better than having the tag full of random keywords
that will rank for a short while, but ultimately result in some bad search engine ju ju.

Luckily, he has a lot of good things going for him.  His site is already mobile optimized.  Just an FYI, if your site isn't mobile
freindly, you have until 4/21 to get on board or suffer the wrath of Google ([the mobile friendly deadline is looming](http://www.firstscribe.com/blog/nine-things-need-know-googles-mobile-friendly-deadline/))
He's also already setup with SSL or HTTPS which, as I learned at Search Marketing Expo, is going to become very important in the
near future.  The UI/UX seems pretty solid as well.

I offered the following suggestions to him to improve:  Make sure the title tags reflect the content and contain keywords, submit that sitemap
and make sure it has the `https://` version of the addresses on there, get a Google My Business map on the page in place of the
regular Google map, and insert some structured data.  I even wrote up the markup because it involves code and I love coding.

A sanitized version of the markup looks like

{% highlight javascript %}
<script type="application/ld+json">
  {
    "@context" : "http://schema.org",
    "@type" : "LocalBusiness",
    "address" : {
      "@type" : "PostalAddress",
      "addressLocality" : "City",
      "addressRegion" : "IN",
      "streetAddress" : "1313 Mockingbird Ln"
    },
    "openingHours" : "Mo, Tu, We, Th, Fr 10:00-18:00",
    "description" : "Computer repair, networking services, and internet hosting serving 46350, 46360, 46304, and surrounding areas.",
    "name": "Business Name",
    "telephone" : "(219) 555-1234"
  }
</script>
{% endhighlight %}

## Now I Play the Waiting Game

So how am I doing?  That's one of the things that I've come to realize while learning SEO.  The results worth getting seem to not happen quickly.
On an old site I used to run, I fell for some black-hat SEO tactics that taught me a quick lesson.  Just a heads up, if your site
is hosted on a server that uses cPanel and you see that "SEO Tools" section just calling out for you to click it, be careful.  I
spent a significant amount of money on one of those $99/month companies that guaranteed more links, more mentions, more traffic, and
more business.  How could I go wrong?

Very easily, actually.  I suddenly had 1000s of links pointing to me and hundreds of "blog posts" mentioning my site by title, but
they were hard to read and the links were coming from less-than-reputable sources.  For the first week, I was getting page views from
around the globe and my ranking was up for all of the keywords I chose, but, like Icarus, I flew too high and fell hard.  Google caught on
to what the experts had done and I was all but blacklisted.  My ranking went down and my visits all but disappeared.  Let me be an example
for you.  If someone tells you that they can get you to Page 1, Rank 1 for $99/month but they won't tell you how or they won't talk to
you in with their voice as opposed to strictly email, run away as fast as you can.  Sure, you might see a temporary boost, but in the long
run you'll wish you hadn't.

## Questions for You

So, now that I've started my transition over into the world of SEO, do you have any advice for me?  Am I on the right track as far as
trying to boost the sites I'm working on or have I completely borked them up?  Since I'm still in the infancy of learning SEO, I am
100% open to suggestion.

Leave your thoughts in the comments or please, feel free to email me or connect with me whichever way works best for you.


