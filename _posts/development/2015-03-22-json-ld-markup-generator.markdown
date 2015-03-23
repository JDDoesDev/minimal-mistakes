---
layout: post
title: "JSON-LD Markup Generator"
modified:
categories: development
excerpt: "The JSON-LD Markup Generator is an ongoing project that allows you to enter in information and generate some schema.org markup that
you can insert into emails, web pages, or anything else you want!"
tags: [JSON-LD, development, SEO schema markup, rich snippets]
image:
  feature:
comments: true
date: 2015-03-22T15:10:35-05:00
---

## JSON-LD for Schema Got You Down?

At SMX West one of the panels I attended that gained more attention from the developer side of me was structured data.  I'm sure if
you've read previous posts, like this one on [The Beauty of JSON-LD](development/beauty-json-ld) then you'd know that JSON-LD
excites the hell out of me.  So I went ahead and made a thing.

## The JSON-LD Generator!

It slices, it dices, it really only produces JSON-LD Markup.

The instructions are simple:

* Select what kind of element you want to use
* Fill out the fields you want to include
* Copy the contents of the textarea to your clipboard
* Test it at [Google's Structured Data Testing Tool](https://developers.google.com/structured-data/testing-tool/)
* Put it wherever you want it to go!

## Why JSON-LD Instead of Standard Markup?

Standard HTML markup is difficult to get right.  There are a ton of `itemprop`, `itemscope`, and `itemtype` attributes that have to be
scattered throughout your page just to get one thing.  With JSON-LD you put the generated script in the `<head>` section of your page
or anywhere inside the HTML email you're sending out and you're done!

## Why ANY Markup at All?

If you use Google (and you do) you may have noticed that some things appear differently.  It happens because of structured data
embedded in the code.  If you have an Android phone then you might notice tha Google knows you better than you do.  This is also
because of structured data in the code.  When an email goes through GMail with structured data, Google picks that data out, and uses
it to tell you when something is going to happen like a concert, a flight, or other events.

In short, it's a good thing to do if you have anything you want people to know about.

## The JSON-LD Structured Data Generator v0.1

Just a note, this is still in beta.  Please report any bugs to [jd@jamesdflynn.com](mailto:jd@jamesdflynn.com) and let me know
your thoughts in the comments.  I'll be adding new data types in the coming days and trying to find better ways to get the data
to you.

If you like it, tell your friends.  If not, tell me!

<div id="formHolder">
  <form id="selector">
    Select the type of markup you want to create:
    <select id="form-selector" name="form-selector">
      <option>---</option>
    </select>
  </form>

  <form id="person" style="display:none;">
    <input type="hidden" data-path="@context" value="http://www.schema.org">
    <input type="hidden" data-path="@type" value="person">
    <label for="name">Name:</label>
    <input id="name" name="name" type="text" data-path="name">
    <label for="jobTitle">Job Title:</label>
    <input id="jobTitle" name="jobTitle" type="text" data-path="jobTitle">
    <label for="url">URL:</label>
    <input id="url" name="url" type="text" data-path="url">
    <input type="hidden" data-path="address.@type" value="PostalAddress">
    <label for="address">Address:</label>
    <input id="address" name="address" type="text" data-path="address.streetAddress">
    <label for="po-box">PO Box:</label>
    <input id="po-box" name="po-box" type="text" data-path="address.postOfficeBoxNumber">
    <label for="addressLocality">City:</label>
    <input id="addressLocality" name="addressLocality" type="text" data-path="address.addressLocality">
    <label for="addressRegion">State/Region:</label>
    <input id="addressRegion" name="addressRegion" type="text" data-path="address.addressRegion">
    <label for="postalCode">Zip/Postal Code:</label>
    <input id="postalCode" name="postalCode" type="text" data-path="address.postalCode">
    <label for="addressCountry">Country:</label>
    <input id="addressCountry" name="addressCountry" type="text" data-path="address.addressCountry">
    <label for="email">Email:</label>
    <input id="email" name="email" type="text" data-path="email">
    <label for="telephone">Telephone (please include country code, +1 for USA):</label>
    <input id="telephone" name="telephone" type="text" data-path="telephone">
    <label for="birthDate">Birth Date (international format YYYY-MM-DD):</label>
    <input id="birthDate" name="birthDate" type="text" data-path="birthDate">
  </form>

  <form id="product" style="display:none;">
    <input type="hidden" data-path="@context" value="http://www.schema.org">
    <input type="hidden" data-path="@type" value="product">
    <label for="brand">Brand:</label>
    <input id="brand" name="brand" type="text" data-path="brand">
    <label for="name">Name:</label>
    <input id="name" name="name" type="text" data-path="name">
    <label for="image">Image (relative or absolute url):</label>
    <input id="image" name="image" type="text" data-path="image">
    <label for="desription">Description:</label>
    <textarea rows="5" cols="50" name="description" data-path="description"></textarea>
    <input type="hidden" data-path="aggregateRating.@type" value="aggregateRating">
    <label for="rating">Rating:</label>
    <input id="rating" name="rating" type="text" data-path="aggregateRating.ratingValue">
    <label for="reviews">Based on how many reviews?</label>
    <input id="reviews" name="reviews" type="text" data-path="aggregateRating.reviewCount">
  </form>
  <form id="event" style="display:none;">
    <input type="hidden" data-path="@context" value="http://www.schema.org">
    <label for="eventType">Select Event Type</label>
    <select name="eventType" type="select" data-path="@type">
      <option value="Event"></option>
      <option value="BusinessEvent"></option>
      <option value="ChildrensEvent"></option>
      <option value="ComedyEvent"></option>
      <option value="DanceEvent"></option>
      <option value="EducationEvent"></option>
      <option value="Festival"></option>
      <option value="FoodEvent"></option>
      <option value="LiteraryEvent"></option>
      <option value="MusicEvent"></option>
      <option value="SaleEvent"></option>
      <option value="SocialEvent"></option>
      <option value="SportsEvent"></option>
      <option value="TheaterEvent"></option>
      <option value="UserInteraction"></option>
      <option value="VisualArtsEvent"></option>
    </select>
    <label for="name">Name:</label>
    <input id="name" name="name" type="text" data-path="name">
    <label for="url">URL:</label>
    <input id="url" name="url" type="text" data-path="url">
    <label for="desription">Description:</label>
    <textarea rows="5" cols="50" name="description" data-path="description"></textarea>
    <label for="startDate">Start Date(mm/dd/yyyy hh:mm am/pm):</label>
    <input id="startDate" name="startDate" type="datetime-local" data-path="startDate" class="start-date">
    <label for="endDate">End Date(mm/dd/yyyy hh:mm am/pm):</label>
    <input id="endDate" name="endDate" type="datetime-local" data-path="endDate" class="end-date">
    <input type="hidden" data-path="location.@type" value="Place">
    <label for="location-name">Venue Name:</label>
    <input id="location-name" name="location-name" type="text" data-path="location.name">
    <label for="location-url">Venue URL:</label>
    <input id="location-url" name="location-url" type="text" data-path="location.sameAs">
    <input type="hidden" data-path="location.address.@type" value="PostalAddress">
    <label for="address">Address:</label>
    <input id="address" name="address" type="text" data-path="location.address.streetAddress">
    <label for="addressLocality">City:</label>
    <input id="addressLocality" name="addressLocality" type="text" data-path="location.address.addressLocality">
    <label for="addressRegion">State/Region:</label>
    <input id="addressRegion" name="addressRegion" type="text" data-path="location.address.addressRegion">
    <label for="postalCode">Zip/Postal Code:</label>
    <input id="postalCode" name="postalCode" type="text" data-path="location.address.postalCode">
    <label for="addressCountry">Country:</label>
    <input id="addressCountry" name="addressCountry" type="text" data-path="location.address.addressCountry">
    <input type="hidden" data-path="offers.@type" value="Offer">
    <label for="offerDesc">Offer Description:</label>
    <input id="offerDesc" name="offerDesc" type="text" data-path="offers.description">
    <label for="offerURL">Offer URL:</label>
    <input id="offerURL" name="offerURL" type="text" data-path="offers.url">
    <label for="offerPrice">Offer Price:</label>
    <input id="offerPrice" name="offerPrice" type="text" data-path="offers.price">
  </form>
  <form id="organization" style="display:none;">
    <input type="hidden" data-path="@context" value="http://www.schema.org">
    <label for="orgType">Select Organization Type:</label>
    <select name="orgType" data-path="@type">
      <option value="Organization"></option>
      <option value="Corporation"></option>
      <option value="EducationalOrganization"></option>
      <option value="GovernmentOrganization"></option>
      <option value="LocalBusiness"></option>
      <option value="NGO"></option>
      <option value="PerformingGroup"></option>
      <option value="SportsTeam"></option>
    </select>
    <label for="name">Name:</label>
    <input id="name" name="name" type="text" data-path="name">
    <label for="url">URL:</label>
    <input id="url" name="url" type="text" data-path="url">
    <label for="desription">Description:</label>
    <textarea rows="5" cols="50" name="description" data-path="description"></textarea>
    <input type="hidden" data-path="address.@type" value="PostalAddress">
    <label for="address">Address:</label>
    <input id="address" name="address" type="text" data-path="address.streetAddress">
    <label for="po-box">PO Box:</label>
    <input id="po-box" name="po-box" type="text" data-path="address.postOfficeBoxNumber">
    <label for="addressLocality">City:</label>
    <input id="addressLocality" name="addressLocality" type="text" data-path="address.addressLocality">
    <label for="addressRegion">State/Region:</label>
    <input id="addressRegion" name="addressRegion" type="text" data-path="address.addressRegion">
    <label for="postalCode">Zip/Postal Code:</label>
    <input id="postalCode" name="postalCode" type="text" data-path="address.postalCode">
    <label for="addressCountry">Country:</label>
    <input id="addressCountry" name="addressCountry" type="text" data-path="address.addressCountry">
    <label for="openingHours">Open Hours (2 letter days and 24 hour time. Example: "Mo, Tu, We, Th, Fr 10:00-18:00" :</label>
    <input id="openingHours" name="openingHours" type="text" data-path="openingHours">
    <input type="hidden" data-path="contactPoint.@type" value="ContactPoint">
    <label for="contactType">Contact Type:</label>
    <input id="contactType" name="contactType" type="text" data-path="contactPoint.contactType">
    <label for="telephone">Telephone:</label>
    <input id="telephone" name="telephone" type="text" data-path="contactPoint.telephone">
  </form>
</div>
<div class="output">
  <textarea class="json">

  </textarea>
  <div id="buttonHolder">
    <button id="reset">
      Reset Form
    </button>
  </div>
</div>


<script>
  $(function() {
    //function to populate the form selector based
    //on the forms that are available.

    $('form').each(function() {
      if ($(this).attr('id') != 'selector') {
        var option = $(this).attr('id');
        $('select#form-selector').append('<option value="' + option + '">' + option.toUpperCase() + '</option>');
      };
    });
    $('option').each(function() {
      console.log($(this).html());
      if (!$(this).html() || $(this).html() === "") {
        $(this).html($(this).val());
      }
    });
    var selected;
    var old;

    //changes the displayed form based on the selection
    $("#selector").change(function() {
      old = selected;
      selected = "#" + $("#selector option:selected").val();
      if (old) {//closes the old form
        $(old).slideToggle();
      }
      $(selected).slideToggle();
      $("pre").html("");
      // clears out the <pre> container for the next one
      //cycles through the elements of the form and
      //clears the value on change.
      $('input,textarea').each(function() {
        if ($(this).attr('type') != 'hidden') {
          $(this).val("");
        };
      });
      var element = {};
      //instantiate the object

      // fire when a key is pressed in an input or textarea
      $(selected + ' input,' + selected + ' textarea,' + selected + ' select').keyup(function() {
        // this iterates through the whole form.  @TODO see if there's a better way
        element = {};
        // this is highly inefficient, but it keeps things in order
        $(selected + ' input,' + selected + ' textarea,' + selected + ' select').each(function() {
          //selects the data-path attr and splits it if necessary.
          //the first is checked to see if it's alreay the key
          //and the second is used as the inner array
          var path = $(this).data('path').split('.'),
              currentData =
              element;
          for (var i = 0; i < path.length - 1; i++) {
            if (!currentData[path[i]]) {
              //if the first part of data-path doesn't exist then it becomes
              //the key for this array
              currentData[path[i]] = {};
            }
            //console.log(currentData[path[i]]);
            currentData = currentData[path[i]];
          }
          //if it's empty, then it doesn't exist
          currentData[path[path.length - 1]] = ($(this).val().length > 0 ? $(this).val() : null);
          if (currentData[path[path.length - 1]] === null) {
            //get rid of the data that doesn't exist
            delete currentData[path[path.length - 1]];
          }
          //prep it for output
          $(".json").val(JSON.stringify(element, null, 2));
        });
      });
    });

    //this function clears the <pre> and all fields
    $("#reset").click(function() {
      $("pre").html("");
      $('input,textarea,select').each(function() {
        if ($(this).attr('type') != 'hidden') {
          $(this).val("");
        }
      });
    });
  });
</script>
