<h1>Posts Archive</h1>
<ul>
  {% for post in site.posts %}
    <li><a href="{{post.url}} style="color: #159957;">{{post.title}}</a></li>
  {% endfor %}
</ul>
