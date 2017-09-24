---
layout: homepage
---

<div class="changelog">
  <main class="fix-blue">
    <div class="pt-3 pt-sm-3">
      {% include menu.html %}
    </div>
  </main>

  <div class="changelog-image mb-5">
  </div>

  <div class="container">
    <div class="row">
      <div class="col">
        <h2 class="text-center font-weight-normal mb-4">All the important changes since launch</h2>
      </div>
    </div>
    <div class="row mb-5">
      <div class="col-12 col-sm-4">
        <div class="promo-box px-3 py-3">
          <h3>Want to receive this by email?</h3>
          <p class="pb-0 mb-0">Subscribe to <a href="https://tinyletter.com/monicahq">the newsletter</a>.</p>
        </div>
      </div>
      <div class="col-12 col-sm-4">
        <div class="promo-box px-3 py-3">
          <h3>Want more details?</h3>
          <p class="pb-0 mb-0">Read the <a href="https://github.com/monicahq/monica/blob/master/CHANGELOG">exhaustive release notes</a>.</p>
        </div>
      </div>
      <div class="col-12 col-sm-4">
        <div class="promo-box px-3 py-3">
          <h3>Want to submit an idea?</h3>
          <p class="pb-0 mb-0">Create an <a href="https://github.com/monicahq/monica/issues">issue on GitHub</a>.</p>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="changes">
        {% for change in site.data.changes %}
          <h3 class="font-weight-normal">{{ change.date | date_to_long_string }}</h3>
          <ul class="mb-5">
            {% for data in change.list-changes %}
            <li>{{ data.change }}</li>
            {% endfor %}
          </ul>
        {% endfor %}
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col bio">
        <h3 class="text-center font-weight-normal">Create your account for free</h3>
        <p class="text-center mb-4">Or install Monica on a server that you own</p>
        <div class="text-center mb-3">
          <a href="#" class="btn btn-primary px-4 py-3">Create account</a>
        </div>
        <p class="text-center font-weight-light mb-5">Already trusted by 10,000+ users.</p>
      </div>
    </div>
  </div>
</div>