---
layout: post
title: "Securing Your Sites for HTTPS"
modified:
categories: development
excerpt: "The world is a dangerous place.  There is a lot of information out there, and some of it is more sensitive than the rest.  Your name, your emails, your passwords, social security, birth dates, credit card numbers, etc.  Many people just type their info into the forms with no thought"
tags: [web development, ssl, https]
comments: true
image:
  feature:
date: 2015-03-29T15:17:14-05:00
---

## Why Do You Need to be Secure?

The world is a dangerous place.  There is a lot of information out there, and some of it is more sensitive than the rest.  Your name, your emails, your passwords, social security, birth dates, credit card numbers, etc.  Many people just type their info into the forms with no thought as to what risk is being taken, but others, like myself, won't even enter an email address without seeing the padlock in the URL bar.

<div style="padding: 3px; background-color: #fefefe; border: 1px solid black; text-align: center; width: 100px; margin: auto;">
  <img src="/images/padlock.png" alt="Safety First!" />
</div>

But where does that padlock come from and what does it mean?

## Lock It Down!

The padlock is a promise.  It's a promise that data is secure while on your site.  It's a promise that you have made the effort to protect your users' information.  Most importantly, it's a promise that you care about your users and you want them to feel safe while on your site.

Gary Illyes ([@methode](http://twitter.com/methode)) made it as clear, as a direct Google representative, that Google was offering a rankings boost for sites with the HTTPS/SSL protocol in effect, citing [Maslow's Hierarchy of Needs](http://www.simplypsychology.org/maslow.html) as one of the driving factors.
<div style="height: 200px; width: 400px; margin: auto; float: left;">
 <img src="/images/MaslowsHierarchyOfNeeds.png" alt="Maslow's Hierarchy of Needs" style="height: 200px; width: auto;"/>
</div>

Some concerns that have been voiced are speed and cost.  Website owners worry that passing their sites through the extra level of protocols will create a delay in getting the content from host to the user's browser.  Gary Illyes had the strongest argument against that concern.  To paraphrase, he said that Google is in the business of being fast.  They are not going to recommend anything that is going to have a noticeable negative effect on the speed.

The other concern, that of cost, really depends on the level of security that a site needs.  I think that everyone can agree that there are different levels of information.  A name and email are not as high priority as, say a credit card or social security number.  With that being said, there are free, shared certificates available, or there are certificates that range in price to the tens of thousands of dollars.

My page, the one you're reading, opted for a free certificate, compliments of [CloudFlare](www.cloudflare.com), however, depending on what information you're collecting from your users, you might want to consider paying for a certificate with a warranty.  A warranty covers the end user, not the site owner, in the event of loss due to fraud or data breech.

## How to Get Secure

The process itself is relatively simple.  From a very, very high level view, all you do is get your certificate and point your site to https instead of http.  The process itself is a bit more involved than that.

I'm going to try and walk through the process I went through for this site, and for one of the sites I work on that uses a content management system behind a content provider as well.

For this small blog, the process was simple:

- Set up a CloudFlare account.
- Change the nameservers over to the provided CloudFlare nameservers
-- This part depends on your hosting provider and DNS provider
- Activate "Flexible SSL"
- Change the links to reflect the change
- Redirect your site to HTTPS (more on this in a bit)

For the larger sites I work on, the process is not really that much more complicated, aside from the size of the site.

- CloudFlare
- Nameservers
- Flexible SSL (or Full if you have your own certificate)
- Change the links
- Redirect

Now how do you redirect?  Good question!

The simplest way to redirect is through an .htaccess file in your site's root directory.  For those unfamiliar, the .htaccess file is the file that contains directives on a directory by directory basis.  Of course, if you have access to your httpd config file, that's really the best way to go.

The standard method for redirecting over to HTTPS through a .htaccess file is
{% highlight html %}

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

{% endhighlight %}

What do those lines mean?  Let's break it down line by line.

`RewriteEngine On` turns on the part of Apache that processes and redirects the URL

`RewriteCond %{HTTPS} off` checks to see if the url contains HTTPS

`RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}` changes the URL over to the new, more secure version.

Pretty simple, right? For many sites, that's all there is to it.

Something else to consider, though, is whether or not your site is behind an accelerator like Varnish and how that might affect your redirects and/or CMS.  The CMS I use at my job, Drupal, relies quite a bit on the `$_SERVER[]` superglobal to tell whether or not the site has been redirected to the HTTPS version.  Our Google Fonts module (@font-your-face) decides whether or not it's going pull content from the http or https version.  In fact, the code itself reads:

{% highlight php %}

if (isset($_SERVER['HTTPS']) && $_SERVER['HTTPS'] == 'on') {
  $base = 'https://fonts.googleapis.com/css?family=';
}

{% endhighlight %}

The problem lies in the fact that `$_SERVER['HTTPS']` is not set behind Varnish.  Instead, we have `$_SERVER['HTTP_X_FORWARDED_PROTO']` with a value of either `http` or `https` so, we can use that to our advantage in an IF/ELSE statement.  The one that I use is:

{% highlight php %}

if ( (isset($_SERVER["HTTPS"]) && strtolower($_SERVER["HTTPS"]) == "on")
  || (isset($_SERVER["HTTP_X_FORWARDED_PROTO"]) && $_SERVER["HTTP_X_FORWARDED_PROTO"] == "https")
  || (isset($_SERVER["HTTP_HTTPS"]) && $_SERVER["HTTP_HTTPS"] == "on")
  )  {
  $_SERVER["HTTPS"] = "on";
}

{% endhighlight %}

which covers pretty much every possibility and passes the right value through.

## In Summary

It's really not all that difficult to get setup, nor is it expensive at all depending on your needs.  So, go forth, lock those padlocks, and make your users feel secure.  Be sure to clear your caches and check to make sure none of your images are hard-coded with `http` addresses.  A good tool to use to check why you might not be getting the green padlock is [Why No Padlock](www.whynopadlock.com) which will check your site and tell you what might be going on.

Got any other suggestions on how else to secure your sites?  Let me know.

<div style="clear:both"></div>
