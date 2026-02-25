---
layout: post
courses: CSSE
title: Night at Muesem Blog
permalink: /natmblg
author: Ahmad Sediqi 
---

# Night at the Muesem
This page talks about the stuff that happened in N@tm tri 1.

---

**Murder Mystery:** 
This is what my class was presenting, it was a game that was in my opinion very poorly built.

---

**CSP:** 
I remember that one of the CSP students told me that they added a AI and Camera on their site, that made me realize that the distance in skills between Amateurs and Exprience is massive.

---

**MoodLife**: 
This is the site made by CSP student Shayan and his group, it uses AI to detect your mood and it shows you what your mood is and this really facinated me. 

---

## Summary
The Night at the Muesem was a really great learning experience which helped me understand the capability of what we can achieve. It was also a good event to interact with other students all from different grades and talk about what they were doing in their classes

---

### Here are Some photos of Me and the projects at N@tm  

<style>
.natm-gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  margin: 20px 0;
}
.natm-gallery img {
  width: 100%;
  aspect-ratio: 4/3;
  object-fit: cover;
  border-radius: 8px;
  cursor: pointer;
  transition: transform 0.2s, opacity 0.2s;
  opacity: 0.9;
}
.natm-gallery img:hover {
  transform: scale(1.03);
  opacity: 1;
}
.natm-lb {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.88);
  z-index: 9999;
  align-items: center;
  justify-content: center;
  backdrop-filter: blur(8px);
}
.natm-lb.open { display: flex; }
.natm-lb img {
  max-width: 90vw;
  max-height: 85vh;
  border-radius: 10px;
  object-fit: contain;
  box-shadow: 0 20px 60px rgba(0,0,0,0.7);
}
.natm-lb-close {
  position: fixed; top: 18px; right: 22px;
  background: rgba(255,255,255,0.15); border: none;
  color: #fff; font-size: 1.4rem; width: 40px; height: 40px;
  border-radius: 50%; cursor: pointer; display: flex;
  align-items: center; justify-content: center;
}
.natm-lb-close:hover { background: rgba(255,255,255,0.28); }
.natm-nav {
  position: fixed; top: 50%; transform: translateY(-50%);
  background: rgba(255,255,255,0.12); border: none; color: #fff;
  font-size: 1.3rem; width: 44px; height: 44px; border-radius: 50%;
  cursor: pointer; display: flex; align-items: center; justify-content: center;
}
.natm-nav:hover { background: rgba(255,255,255,0.25); }
.natm-nav.prev { left: 16px; }
.natm-nav.next { right: 16px; }
.natm-lb-caption {
  position: fixed; bottom: 20px; left: 50%; transform: translateX(-50%);
  color: rgba(255,255,255,0.6); font-size: 0.8rem; font-family: monospace;
  background: rgba(0,0,0,0.5); padding: 6px 14px; border-radius: 20px;
}
</style>

<div class="natm-gallery" id="natmGallery">
  <img src="{{site.baseurl}}/images/natm/mg.JPG"      alt="Student playing top-down game" onclick="natmOpen(0)">
  <img src="{{site.baseurl}}/images/natm/image2.jpeg" alt="HawkNest demo setup"            onclick="natmOpen(1)">
  <img src="{{site.baseurl}}/images/natm/image3.jpeg" alt="Snakes and Ladders game"        onclick="natmOpen(2)">
  <img src="{{site.baseurl}}/images/natm/image4.jpeg" alt="Hunger Heroes app"              onclick="natmOpen(3)">
  <img src="{{site.baseurl}}/images/natm/image5.jpeg" alt="NYC Trip Planner"               onclick="natmOpen(4)">
  <img src="{{site.baseurl}}/images/natm/image6.jpeg" alt="AI Student Insights Poll"       onclick="natmOpen(5)">
  <img src="{{site.baseurl}}/images/natm/image7.JPG"  alt="MoodLife wellness app"          onclick="natmOpen(6)" style="grid-column: span 3; aspect-ratio: 16/5;">
</div>

<div class="natm-lb" id="natmLb" onclick="natmBgClose(event)">
  <button class="natm-lb-close" onclick="natmClose()">✕</button>
  <button class="natm-nav prev"  onclick="natmNav(-1, event)">&#8592;</button>
  <img id="natmLbImg" src="" alt="">
  <button class="natm-nav next"  onclick="natmNav(1, event)">&#8594;</button>
  <div class="natm-lb-caption" id="natmCaption"></div>
</div>

<script>
(function(){
  const imgs = [
    { src: '{{site.baseurl}}/images/natm/mg.JPG',      cap: '1 / 7 — Top-Down Game' },
    { src: '{{site.baseurl}}/images/natm/image2.jpeg', cap: '2 / 7 — HawkNest Demo' },
    { src: '{{site.baseurl}}/images/natm/image3.jpeg', cap: '3 / 7 — Snakes & Ladders' },
    { src: '{{site.baseurl}}/images/natm/image4.jpeg', cap: '4 / 7 — Hunger Heroes' },
    { src: '{{site.baseurl}}/images/natm/image5.jpeg', cap: '5 / 7 — NYC Trip Planner' },
    { src: '{{site.baseurl}}/images/natm/image6.jpeg', cap: '6 / 7 — AI Insights Poll' },
    { src: '{{site.baseurl}}/images/natm/image7.JPG',  cap: '7 / 7 — MoodLife App' },
  ];
  let cur = 0;
  window.natmOpen = function(i) {
    cur = i;
    document.getElementById('natmLbImg').src = imgs[i].src;
    document.getElementById('natmCaption').textContent = imgs[i].cap;
    document.getElementById('natmLb').classList.add('open');
    document.body.style.overflow = 'hidden';
  };
  window.natmClose = function() {
    document.getElementById('natmLb').classList.remove('open');
    document.body.style.overflow = '';
  };
  window.natmBgClose = function(e) {
    if (e.target === document.getElementById('natmLb')) natmClose();
  };
  window.natmNav = function(dir, e) {
    e.stopPropagation();
    cur = (cur + dir + imgs.length) % imgs.length;
    const img = document.getElementById('natmLbImg');
    img.style.opacity = '0';
    setTimeout(function(){
      img.src = imgs[cur].src;
      document.getElementById('natmCaption').textContent = imgs[cur].cap;
      img.style.opacity = '1';
    }, 120);
    img.style.transition = 'opacity 0.12s';
  };
  document.addEventListener('keydown', function(e){
    if (!document.getElementById('natmLb').classList.contains('open')) return;
    if (e.key === 'Escape') natmClose();
    if (e.key === 'ArrowLeft')  natmNav(-1, {stopPropagation:function(){}});
    if (e.key === 'ArrowRight') natmNav(1,  {stopPropagation:function(){}});
  });
})();
</script>