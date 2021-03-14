---
title: Search
description: "Search this site"
layout: page
permalink: /search/
tipue_search_active: true
exclude_from_search: true
---


<div class="page">

{% capture page_subtitle %}
 {% include page/searchbox.html %}
{% endcapture %}

{% include page/title.html title=page.title subtitle=page_subtitle %}

<div id="tipue_search_content"></div> 
<script>
$(document).ready(function() {
  $('#tipue_search_input').tipuesearch({
    'wholeWords' : false,
    'showTime' : false,
    'minimumLength' : 2  });
});
</script>


</div>
