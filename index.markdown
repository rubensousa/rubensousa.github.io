---
layout: page
title: Rúben Sousa
---
I'm a student of Telecommunications and Informatics at University of Minho hoping to finish my master's degree on 2017.
I'm also a part-time Android developer freelancer.

I spend a lot of my free time developing some projects in Android and Java, some of which are open source and available on my GitHub account:
[https://github.com/rubensousa](https://github.com/rubensousa)

You can also find my Android apps in Google Play: [https://play.google.com/store/apps/developer?id=rubensousa](https://play.google.com/store/apps/developer?id=rubensousa)

This is my personal blog, where I'll be posting content related to software engineering.

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
   <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>
   {{ post.content | split:'<!--break-->' | first }}
   {% if post.content contains '<!--break-->' %}
      <a href="{{ post.url }}">Read more</a>
   {% endif %}
   </div>
   <hr>
{% endfor %}