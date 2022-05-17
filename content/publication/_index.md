---
title: Publications
cms_exclude: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
#   4 = Citation
view: 4

# Optional header image (relative to `static/media/` folder).
header:
  caption: ""
  image: ""
---

Here are the references to my academic papers and client project reports since 2020. If you are looking for a complete list of my publications go to the {{< staticref "https://www.zotero.org/pjastam/" "newtab" >}}Zotero website{{< /staticref >}}.

<script>
for (let i = 2022; i >= 2022; i--) {
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
