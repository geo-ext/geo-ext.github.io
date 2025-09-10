---
layout: page
title: ""
permalink: /
---

<!-- Leaflet CSS -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />

<style>
/* 隐藏 Minima 页脚，避免底部重复块 */
.site-footer { display: none; }

/* 简洁列表 + 地图样式 */
.intro { margin:.75rem 0 0; color:#666; font-size:.95rem }
.archive-list { list-style:none; padding-left:0; margin:1rem 0 2rem; }
.archive-list li { margin:.5rem 0; }
.archive-list a { text-decoration:none; font-weight:600; }
.archive-list a:hover { text-decoration:underline; }
#map { height: 360px; border-radius: 12px; margin: 1rem 0 0; }
</style>

<p class="intro">ECIR co-located workshop series on Geographic Information Extraction from Texts.</p>

<ul class="archive-list">
  <li><a href="https://geo-ext.github.io/GeoExT2023/">First GeoExT Workshop — ECIR 2023, Dublin</a></li>
  <li><a href="https://geo-ext.github.io/GeoExT2024/">Second GeoExT Workshop — ECIR 2024, Glasgow</a></li>
  <li><a href="https://geo-ext.github.io/GeoExT2025/">Third GeoExT Workshop — ECIR 2025, Lucca</a></li>
</ul>

<div id="map" role="img" aria-label="Workshop locations: Dublin, Glasgow, Lucca"></div>

<!-- Leaflet JS -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script>
  // 开启滚轮缩放（scrollWheelZoom: true）
  const map = L.map('map', { scrollWheelZoom: true });

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);

  const editions = [
    { name:'First GeoExT Workshop — ECIR 2023, Dublin',  lat:53.3498, lon:-6.2603, url:'https://geo-ext.github.io/GeoExT2023/' },
    { name:'Second GeoExT Workshop — ECIR 2024, Glasgow', lat:55.8642, lon:-4.2518, url:'https://geo-ext.github.io/GeoExT2024/' },
    { name:'Third GeoExT Workshop — ECIR 2025, Lucca',    lat:43.8420, lon:10.5080, url:'https://geo-ext.github.io/GeoExT2025/' }
  ];

  const bounds = [];
  editions.forEach(e => {
    bounds.push([e.lat, e.lon]);
    L.marker([e.lat, e.lon]).addTo(map)
      .bindPopup('<a href="'+e.url+'">'+e.name+'</a>');
  });
  map.fitBounds(bounds, { padding: [24,24] });
</script>

<noscript>Map requires JavaScript enabled.</noscript>
