---
layout: page
title: Youndo Do
---

I am a PhD student in the [Intelligence for Advanced Nuclear Laboratory](https://sites.gatech.edu/ifanlab/) at [Georgia Institute of Technology](https://www.gatech.edu/). Before joining Georgia Tech, I worked as an AI Research Engineer at Netmarble and Vespa AI Research Group for 3 years.

My research focuses on Reinforcement Learning, Interactive Learning, and Generalizable Manipulation. I am interested in developing robots to perform physical tasks that require adaptability and learning from interaction.

---

## News

<div class="container" style="max-width: 750px;">
  <div class="list-group">
    {% assign latest_news = site.data.news | slice: 0, 5 %}
    {% assign older_news = site.data.news | slice: 5, site.data.news.size %}

    {% for news in latest_news %}
    <div class="list-group-item small">
      <strong>{{ news.date }}</strong> {{ news.content }}
    </div>
    {% endfor %}

    <div id="older-news" style="display: none;">
      {% for news in older_news %}
      <div class="list-group-item small">
        <strong>{{ news.date }}</strong> {{ news.content }}
      </div>
      {% endfor %}
    </div>

  </div>

{% if older_news.size > 0 %}
<button id="toggle-news" class="btn btn-outline-primary mt-3">Show More ▽</button>
{% endif %}

</div>

<script>
  document.getElementById("toggle-news").addEventListener("click", function() {
    var olderNews = document.getElementById("older-news");
    if (olderNews.style.display === "none") {
      olderNews.style.display = "block";
      this.textContent = "Show Less △";
    } else {
      olderNews.style.display = "none";
      this.textContent = "Show More ▽";
    }
  });
</script>

---
