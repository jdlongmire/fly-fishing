---
title: Fly Reference
parent: Flies
nav_order: 1
---

# Fly Reference

Every pattern in one place — type it or filter it. Driven by [`_data/flies.yml`](https://github.com/jdlongmire/fly-fishing/blob/main/_data/flies.yml); add a fly there and it shows up here. Click a column header to sort; some rows link to a full write-up.

The **▶ clip** links jump to the moment each pattern is shown in the [Wild Bearings South Holston webcast](https://youtu.be/z3ZacYADy7g) (timestamps are approximate). The video is theirs — these are deep-links to the original, nothing is rehosted.

<input type="text" id="fly-search" placeholder="Search flies (name, imitates, notes)…" aria-label="Search flies" style="width:100%;max-width:32rem;padding:.5rem .7rem;margin:.5rem 0 1rem;border:1px solid #ccc;border-radius:.4rem;font-size:1rem;">

<div id="fly-facets" style="margin-bottom:1rem;display:flex;flex-wrap:wrap;gap:.4rem;"></div>

<table id="fly-table" class="fly-table">
  <thead>
    <tr>
      <th data-key="name">Fly</th>
      <th data-key="type">Type</th>
      <th data-key="imitates">Imitates</th>
      <th data-key="sizes">Sizes</th>
      <th data-key="season">Season</th>
      <th data-key="bead">Bead</th>
      <th data-key="notes">Notes</th>
      <th>Watch</th>
    </tr>
  </thead>
  <tbody>
  {% for f in site.data.flies %}
    <tr data-type="{{ f.type }}"
        data-search="{{ f.name | append: ' ' | append: f.imitates | append: ' ' | append: f.notes | append: ' ' | append: f.type | downcase | escape }} {{ f.waters | join: ' ' | downcase | escape }}">
      <td>{% if f.page %}<a href="{{ f.page | relative_url }}">{{ f.name }}</a>{% else %}{{ f.name }}{% endif %}</td>
      <td><span class="fly-tag">{{ f.type }}</span></td>
      <td>{{ f.imitates }}</td>
      <td>{{ f.sizes }}</td>
      <td>{{ f.season }}</td>
      <td>{{ f.bead }}</td>
      <td>{{ f.notes }}</td>
      <td>{% if f.video %}<a href="{{ f.video }}" target="_blank" rel="noopener" title="Jump to this pattern in the source video">▶ clip</a>{% endif %}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>

<p id="fly-count" style="color:#666;font-size:.9rem;margin-top:.5rem;"></p>

<style>
.fly-table{width:100%;border-collapse:collapse;font-size:.92rem}
.fly-table th,.fly-table td{border-bottom:1px solid #e6e6e6;padding:.45rem .55rem;text-align:left;vertical-align:top}
.fly-table th{cursor:pointer;white-space:nowrap;user-select:none}
.fly-table th:hover{color:#2b6cb0}
.fly-tag{display:inline-block;background:#eef3f8;color:#2b5876;border-radius:.3rem;padding:.05rem .4rem;font-size:.8rem;white-space:nowrap}
.facet-btn{cursor:pointer;border:1px solid #cbd5e0;background:#fff;border-radius:1rem;padding:.2rem .7rem;font-size:.85rem}
.facet-btn.active{background:#2b6cb0;color:#fff;border-color:#2b6cb0}
</style>

<script>
(function(){
  var table=document.getElementById('fly-table');
  var rows=Array.prototype.slice.call(table.tBodies[0].rows);
  var search=document.getElementById('fly-search');
  var facets=document.getElementById('fly-facets');
  var count=document.getElementById('fly-count');
  var activeType='all';

  var types=['all'].concat(rows.map(function(r){return r.dataset.type;})
    .filter(function(v,i,a){return a.indexOf(v)===i;}).sort());
  types.forEach(function(t){
    var b=document.createElement('button');
    b.className='facet-btn'+(t==='all'?' active':'');
    b.textContent=t; b.dataset.type=t;
    b.onclick=function(){activeType=t;
      Array.prototype.forEach.call(facets.children,function(c){c.classList.toggle('active',c.dataset.type===t);});
      apply();};
    facets.appendChild(b);
  });

  function apply(){
    var q=search.value.trim().toLowerCase();
    var shown=0;
    rows.forEach(function(r){
      var okType=activeType==='all'||r.dataset.type===activeType;
      var okText=!q||r.dataset.search.indexOf(q)>-1;
      var vis=okType&&okText; r.style.display=vis?'':'none'; if(vis)shown++;
    });
    count.textContent=shown+' of '+rows.length+' patterns';
  }
  search.addEventListener('input',apply);

  var sortState={};
  Array.prototype.forEach.call(table.tHead.rows[0].cells,function(th,idx){
    th.addEventListener('click',function(){
      var asc=sortState[idx]=!sortState[idx];
      rows.sort(function(a,b){
        var x=a.cells[idx].innerText.toLowerCase(),y=b.cells[idx].innerText.toLowerCase();
        return x<y?(asc?-1:1):x>y?(asc?1:-1):0;
      });
      rows.forEach(function(r){table.tBodies[0].appendChild(r);});
    });
  });
  apply();
})();
</script>
