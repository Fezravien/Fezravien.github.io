---
layout: page
title: About
permalink: /about/
published: true
---

<div class="page" markdown="1">
{% capture page_subtitle %}
<img
    class="me"
    alt="{{ author.name }}"
    src="{{ site.author.photo | relative_url }}"
    srcset="{{ site.author.photo2x | relative_url }} 2x"
/>
{% endcapture %}

{% include page/title.html title=page.title subtitle=page_subtitle %}

## Hi there š

Iām currently learning at `yagom academy` - iOS CAMP 2nd š±

</div>
