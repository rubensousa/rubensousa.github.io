---
layout: page
title: Rúben Sousa
---
I'm an Android developer currently freelancing.

I spend a lot of my free time developing some projects in Android and Java, some of which are open source and available on my GitHub account:
[https://github.com/rubensousa](https://github.com/rubensousa)

You can also find my Android apps in Google Play: [https://play.google.com/store/apps/dev?id=7082193994052369988](https://play.google.com/store/apps/dev?id=7082193994052369988)

My most recent app is a helper for a European lottery called Euromillions: [https://play.google.com/store/apps/details?id=io.github.rubensousa.euromillions](https://play.google.com/store/apps/details?id=io.github.rubensousa.euromillions)

### Stuff that I'm currently learning

- Android testing (Espresso and JUnit tests)
- Dependency injection with Dagger2

<br>
<br>
<br>

# Recent articles

{% for post in site.posts limit:4 %}
   <div class="post-preview">
   <h3><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h3>
    <h3><span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span></h3>
    <br>
   {{ post.content | split:'<!--break-->' | first }}
   {% if post.content contains '<!--break-->' %}
      <a href="{{ post.url }}">Read more</a>
   {% endif %}
   </div>
   <hr>
{% endfor %}