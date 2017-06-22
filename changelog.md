---
layout: satellite
title: All the major changes since launch
class: changelog
page_icon: changelog/destroymachine.png
---

Want to receive those changes by email? Subscribe to
[the newsletter](https://tinyletter.com/monicahq)! It's sent once a week on
Sunday.

Only the major changes are displayed here. For a more exhaustive list, refer to
[the official changelog](https://github.com/monicahq/monica/blob/master/CHANGELOG).
You can also follow [the roadmap](https://github.com/monicahq/monica/projects/1)
if you want, or [submit an idea](https://github.com/monicahq/monica/issues).

<div class="changes">
{% for change in site.data.changes %}
  <h3>{{ change.date | date_to_long_string }}</h3>
  <ul>
    {% for data in change.list-changes %}
    <li>{{ data.change }}</li>
    {% endfor %}
  </ul>
{% endfor %}
</div>