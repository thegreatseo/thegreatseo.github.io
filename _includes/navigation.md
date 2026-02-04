{% for link in site.data.navigation.main %}
    <a href="{{ link.url }}"
        class="nav-item {% if page.url == link.url %}active{% endif %}">
        {{ link.title }}
    </a>
{% endfor %}