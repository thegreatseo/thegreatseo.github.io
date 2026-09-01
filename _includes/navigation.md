{% for link in site.data.navigation.main %}
    <a href="{{ link.url }}"
        class="nav-item {% if page.url == link.url %}active{% endif %}"
        {% if page.url == link.url %}aria-current="page"{% endif %}>
        {{ link.title }}
    </a>
{% endfor %}
