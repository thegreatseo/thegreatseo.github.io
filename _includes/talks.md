<div class="talks-container">
  {% assign talks_by_year = site.data.talks.main | group_by: "year" %}
  {% for year_group in talks_by_year %}
    <div class="year-block">
      <h2 class="year-heading">{{ year_group.name }}</h2>
      
      <div class="talk-list">
        {% for talk in year_group.items %}
          <div class="talk-item">
            <div class="talk-date">
                <span class="day-month">
                    {% assign date_parts = talk.date | split: " " %}
                    {{ date_parts[0] | slice: 0, 3 }} {{ date_parts[1] }}
                </span>
            </div>
            
            <div class="talk-content">
              <h3 class="talk-title">{{ talk.title }}
                {% if talk.type %}
                    &nbsp;<span class="talk-badge">{{ talk.type }}</span>
                {% endif %}
              </h3>
              <div class="talk-metadata">
                <span class="talk-event"><strong>{{ talk.event }}</strong></span>
                <span class="talk-location">
                  <i class="fa-solid fa-location-dot"></i> {{ talk.venue }}, {{ talk.city }}{% if talk.country %}, {{ talk.country }}{% endif %}
                </span>
              </div>

              <div class="talk-links">
                {% if talk.notice %}
                  <a href="{{ talk.notice }}" target="_blank"><i class="fa-solid fa-circle-info"></i> Notice</a>
                {% endif %}
                {% if talk.slide %}
                  <a href="{{ talk.slide | relative_url }}" target="_blank"><i class="fa-solid fa-file-powerpoint"></i> Slides</a>
                {% endif %}
                {% if talk.poster %}
                  <a href="{{ talk.poster | relative_url }}" target="_blank"><i class="fa-solid fa-image"></i> Poster</a>
                {% endif %}
                {% if talk.video %}
                  <a href="{{ talk.video }}" target="_blank"><i class="fa-solid fa-video"></i> Video</a>
                {% endif %}
              </div>
            </div>
          </div>
        {% endfor %}
      </div>
    </div>
  {% endfor %}
</div>