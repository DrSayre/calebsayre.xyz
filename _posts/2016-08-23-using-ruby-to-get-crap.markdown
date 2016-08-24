---
layout: post
title:  "Using Ruby to get Crap"
date:   2016-08-22 22:13:03 -0400
categories: ruby
---
> This was orignally written on February 23, 2015 for my company's Confluence.

![Box of Crap]({{ site.url }}/assets/unopened_crap.jpg)

*What is in this box? You will need to keep reading to find out...*

## What is this about?

Once a month or so, [Woot!](http://woot.com) has a "Woot-off". What this means is instead of having only one item on their home page, they will change new items through out the day as items sell out. For added fun, Woot! will occasionally offer "bags of crap". This isn't a litteral bag of crap, but a grab bag that could have anything in it. A bag of crap cost $5, but after shipping and taxes, a bag of crap cost $10.60.

Getting one is really hard. They literally sell out in seconds (as I was able to verify in trying to get one). There seems to be 2 ways to get a bag of crap: checking Woot! at just the right time or constantly pressing refreshing the page until crap appears.

## There must be a better way!
Most of us at Suran love checking various daily deals sites ([meh.com](http://meh.com), [slickdeals.com](http://slickdeals.com), etc.) as this seems to be a popular topic on almost a daily basis; however, we have better things to do than to keep refreshing the page for the chance to spend $10 on what could end up being a bag of pipe cleaners. There must be a better way. It just so happened [Danny](http://dannypeters.me) sent me a [blog post about web scraping](https://www.chrismytton.uk/2015/01/19/web-scraping-with-ruby/) while the January Woot-Off was in progress! With this blog post I was able to create a very simple script that checks if the current item for sell has "Crap" in it, if it does, it will open the page otherwise it will check again until the item does have crap in the name. There is the obvious flaw that should the item for sell has "crap" in the name, but is not a bag of crap, it will give off a false positive. An example of this is something to do with s**crap**booking.

> If the item does not have crap in the name, we will check for the percent remaining and print the name of item and percent remaining to screen if it's different from the previous check.

We are able to easily check the item and percent remaining by opening the Woot! home page using the OpenURI wrapper and using the Nokogiri gem to parse the html. Nokogiri is the only gem needed for this script, you can get it by doing this:

{% highlight bash %}
	gem install nokogiri
{% endhighlight %}

We can find the item name and percent remaining by searching for the fn and percent-remaining classes. [Here is the link to the final code I used](https://github.com/DrSayre/woot) (feel free to hack on it if you want). When the page opens, you need to add it to the cart and checkout. Here is a screen shot of the output from the script:

![output]({{ site.url }}/assets/woot_code.jpeg)

## Problems

A big issue I ran into was when the page opens and I added the item to the cart, I would need to log in again to checkout. If you read the message board on Woot! or the comments section, you will find a lot of people have this problem. This was probably a big reason why I did not get a bag of crap until the February Woot-Off. A work around I found was to have your browser have your login credentials stored and not use the Amazon login link.  Normally I like to login through Amazon on Woot, but that takes a little longer to sign in. If you have your browser set up right, when you log in after clicking checkout you will only need to click the log in link.

Also at times even when the script would open up the link, the current bag of crap would already be sold out.

## Victory!

By trying at a non-peek hour, I was finally able to get a bag of crap. So here it is, my bag of crap:

![Crap]({{ site.url }}/assets/crap.jpg)

### Contents
* Sticker for my F5 key
* Ear piece
* 12 pack of Valentine Erasers
* 2 pack of Valentine Ducks
* Mystery bag
* 9-in-1 Key Ring Tool
* Some kind of Shirt Woot comic book

{% if site.disqus_shortname %}
  {% include disqus_comments.html %}
{% endif %}