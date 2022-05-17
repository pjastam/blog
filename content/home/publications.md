---
# An instance of the Pages widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: pages

# Activate this widget? true/false
active: true

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 90

title: Recent Publications
subtitle: ''

content:
  # Filter on criteria
  filters:
    folders:
      - publication
    tag: ''
    category: ''
    publication_type: ''
    author: ''
    exclude_featured: yes
    exclude_future: yes
    exclude_past: yes
  # Choose how many pages you would like to display (0 = all pages)
  count: 0
  # Choose how many pages you would like to offset by
  offset: 0
  # Page order: descending (desc) or ascending (asc) date.
  order: desc

design:
  # Choose a view for the listings:
  view: citation
  columns: '2'
---

<!--
{{% callout note %}}
Quickly discover relevant content by [filtering publications](./publication/).
{{% /callout %}}
-->

<script>
for (let i = 2022; i >= 2021; i--) {
    document.write(`<h2 > ${i} </h2>`);
    document.write(`<div id=year${i}>` + `Loading ${i} publications </div>`);

    fetch(`https://api.zotero.org/users/24775/publications/items?format=bib&style=apa&linkwrap=1&itemType=-attachment&q=${i}`)
        .then(function (response) {
            return response.text();
        })
        .then(function (body) {
            document.getElementById("year" + i).innerHTML = body;
        });
    document.write("<br/>")
}
</script>

<div class="see-all">
{{< staticref "https://www.zotero.org/pjastam/" "newtab" >}}See all publications at my Zotero page{{< /staticref >}} <i class="fas fa-angle-right"></i> 
</div>
