{% for tag in site.tags %}

<ul>
    {% for post in recent_posts %}
        <li class="sidebar-post">
            <a title="post.title" href="{{ post.url }}">
                <span>{{ post.date|date("F Y") }}</span><br>
                {{ post.title }}
            </a>
        </li>
    {% endfor %}
</ul>

<h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }} - {{ post.date | date: "%B %Y" }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
