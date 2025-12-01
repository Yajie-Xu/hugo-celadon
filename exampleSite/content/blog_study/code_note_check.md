---
title: "Checking the code"
date: 2021-12-05
summary: "A tiny D3 snippet I use to sanity-check supply–demand adjustments."
image: "/images/work/decarbon.jpg"
---

```html
<svg id="sketch" width="400" height="240"></svg>
<script>
const svg = d3.select("#sketch");
const demand = d3.line()([[20, 30], [380, 200]]);
const supply = d3.line()([[20, 200], [380, 40]]);

svg.append("path").attr("d", demand)
  .attr("stroke", "#7DA2A9").attr("stroke-width", 3).attr("fill", "none"); .attr("stroke", "#7DA2A9").attr("stroke-width", 3).attr("fill", "none"); .attr("stroke", "#7DA2A9").attr("stroke-width", 3).attr("fill", "none"); .attr("stroke", "#7DA2A9").attr("stroke-width", 3).attr("fill", "none");
svg.append("path").attr("d", supply)  .attr("stroke", "#7DA2A9").attr("stroke-width", 3).attr("fill", "none"); .attr("stroke", "#7DA2A9").attr("stroke-width", 3).attr("fill", "none"); .attr("stroke", "#7DA2A9").attr("stroke-width", 3).attr("fill", "none");
  .attr("stroke", "#C0564B").attr("stroke-width", 3).attr("fill", "none");
33
1
2
3
4

</script>
```

Even with synthetic coordinates, this sketch makes it easy to show how adaptive subsidies shift the curves.
