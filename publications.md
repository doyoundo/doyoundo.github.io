---
layout: default
title: Publications
---

<script>
function toggleBibtex(id) {
    const el = document.getElementById(id);
    const isOpen = el.classList.contains('active');

    document.querySelectorAll('.bibtex-wrapper').forEach(b => {
        b.classList.remove('active');
    });

    if (!isOpen) {
        el.classList.add('active');
    }
}

function copyBibtex(textId, button) {
    const text = document.getElementById(textId).innerText;

    navigator.clipboard.writeText(text).then(() => {
        const original = button.innerText;
        button.innerText = "Copied!";
        setTimeout(() => {
            button.innerText = original;
        }, 1500);
    });
}
</script>

<div class="container">
  <main>
    <h1 class="name-header">Publications</h1>

    <p class="intro-text">
      For a complete list, please see my
      <a href="https://scholar.google.com/citations?user=tYwQs18AAAAJ&hl=en&oi=ao">
        Google Scholar
      </a>.
    </p>

    {% for section in site.data.publications %}
      <h2>{{ section.year }}</h2>

      {% for pub in section.papers %}

        {% assign bib_id = section.year | append: '-' | append: forloop.index0 %}

        <div class="entry">
          <div class="pub-entry-flex">

            <!-- MEDIA -->
            <div class="pub-thumbnail">

              {% if pub.video %}
                <video autoplay loop muted playsinline>
                  <source src="{{ pub.video | relative_url }}" type="video/mp4">
                </video>

              {% elsif pub.image %}
                <img src="{{ pub.image | relative_url }}" alt="{{ pub.title }}">
              {% endif %}

            </div>

            <!-- CONTENT -->
            <div class="pub-content">

              <span class="entry-title">{{ pub.title }}</span>

              <div class="entry-meta">
                {{ pub.authors }} <br>
                <em>{{ pub.venue }}</em>, {{ section.year }}.
              </div>

              <!-- LINKS -->
              <div class="entry-links" style="margin-top: 10px;">

                {% if pub.link %}
                  <a href="{{ pub.link }}" target="_blank" class="pub-btn">Paper</a>
                {% endif %}

                {% if pub.bibtex %}
                  <a href="javascript:void(0)"
                     onclick="toggleBibtex('bib-{{ bib_id }}')"
                     class="pub-btn">BibTeX</a>
                {% endif %}

              </div>

              <!-- BIBTEX -->
              {% if pub.bibtex %}
              <div id="bib-{{ bib_id }}" class="bibtex-wrapper">

                <div class="bibtex-header">
                  <span>BIBTEX CITATION</span>

                  <button class="copy-btn"
                    onclick="copyBibtex('bib-text-{{ bib_id }}', this)">
                    Copy
                  </button>
                </div>

                <pre id="bib-text-{{ bib_id }}" class="bibtex-body">
{{ pub.bibtex }}
                </pre>

              </div>
              {% endif %}

            </div>
          </div>
        </div>

      {% endfor %}
    {% endfor %}

  </main>
</div>