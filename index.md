---
layout: home
title: "Soyeon Park"
---

<link rel="stylesheet" href="/assets/css/custom.css">

##### Hi all 👋 I'm Soyeon Park, a Master’s student in Statistics at Northwestern University.<br> Previously I was a Staff Engineer in Evaluation & Analysis Team at <span class="blue-text"><a href="https://semiconductor.samsung.com/">Samsung Electronics</a></span>, specializing in data analysis, automation, and machine learning applications in semiconductor manufacturing.<br>Currently expanding my expertise in statistics and data science with strong interest in robust modeling under limited data. My goal is to contribute to scalable, trustworthy models that address real-world challenges in technology and industry.





<h2 style="margin-top: 50px;">🎓 Education</h2>
<div style="display: flex; align-items: center; gap: 15px; margin-bottom: 15px;">
  <img src="/assets/images/nu_logo.png" alt="NU Logo" width="60px">
  <div>
    <p style="margin: 0;"><strong>Northwestern University,</strong> Evanston, IL</p>
    <p style="margin: 0;">M.S. in Statistics and Data Science (2025 – Present)</p>
  </div>
</div>

<div style="display: flex; align-items: center; gap: 15px; margin-bottom: 15px;">
  <img src="/assets/images/hu_logo.png" alt="HU Logo" width="60px">
  <div>
    <p style="margin: 0;"><strong>Hanyang University,</strong> Seoul, Republic of Korea</p>
    <p style="margin: 0;">B.S. in Nano and Organic Engineering (2012 – 2016)</p>
  </div>
</div>


<h2 style="margin-top: 50px;">🛠️ Technical Skills</h2>

  * <strong>Programming Languages:</strong> Python, R, SQL, Matlab
  * <strong>Libraries:</strong> NumPy, Pandas, SciPy, Spark, scikit-learn, TensorFlow, PyTorch, Keras, matplotlib, Seaborn
  * <strong>Developer & BI Tools:</strong> Git, Tableau, Power BI, Docker, Excel (VBA), LaTeX, Jira, Confluence

<h2 style="margin-top: 50px;">🗂️ Projects</h2>

<div class="projects-grid">

  <div class="project-card">
    <strong style="font-size: 1.05rem;">Capacity and Demand Forecasting for Capital Planning</strong><br>
    <span class="project-subtitle">Using statistical and machine learning models to support budgeting and resource allocation</span><br>
    <img src="/assets/images/project_capacity.png"
    alt="Capacity Forecasting"
    class="project-image"
    onclick="openLightbox(this)">
  </div>


  <div class="project-card">
    <strong style="font-size: 1.05rem;">Transfer Learning Evaluation for Process Monitoring</strong><br>
    <span class="project-subtitle">Adaptive Predictive Modeling for Dynamic Process Monitoring</span><br>
    <img src="/assets/images/project_transfer.png"
    alt="Transfer Learning Project"
    class="project-image"
    onclick="openLightbox(this)">
  </div>


  <div class="project-card">
    <strong style="font-size: 1.05rem;">End-to-End Workflow Automation for Quality Analytics</strong><br>
    <span class="project-subtitle">ETL + feature scoring + dashboards to reduce manual work and downtime</span><br>
    <img src="/assets/images/project_automation.png"
    alt="Workflow Automation Project"
    class="project-image"
    onclick="openLightbox(this)">
  </div>


  <div class="project-card">
    <strong style="font-size: 1.05rem;">Super-Resolution Imaging to Increase Inspection Throughput</strong><br>
    <span class="project-subtitle">Computer vision pipeline to reduce capture time and avoid equipment spend</span><br>
    <img src="/assets/images/project_sr.png"
    alt="Super Resolution Project"
    class="project-image"
    onclick="openLightbox(this)">
  </div>

</div>

<div id="lightbox" onclick="closeLightbox()">
  <div id="lightbox-inner" onclick="event.stopPropagation()">
    <img id="lightbox-img" alt="Expanded image">
  </div>
</div>



<script>
let zoom = 1;
let tx = 0, ty = 0;                 // translate (pan)
const ZOOM_MIN = 1;
const ZOOM_MAX = 4;
const ZOOM_STEP = 0.12;

let isDragging = false;
let startX = 0, startY = 0;
let startTx = 0, startTy = 0;

function applyTransform() {
  const img = document.getElementById("lightbox-img");
  img.style.transform = `translate(${tx}px, ${ty}px) scale(${zoom})`;
}

function resetTransform() {
  zoom = 1;
  tx = 0; ty = 0;
  applyTransform();
}

function openLightbox(imgEl) {
  const lightbox = document.getElementById("lightbox");
  const lightboxImg = document.getElementById("lightbox-img");

  lightboxImg.src = imgEl.src;
  resetTransform();

  lightbox.style.display = "flex";
  document.body.style.overflow = "hidden";
}

function closeLightbox() {
  document.getElementById("lightbox").style.display = "none";
  document.body.style.overflow = "";
}

function clampPan() {
  // 너무 멀리 드래그해서 이미지가 완전히 사라지지 않게 "대충" 제한
  // (정교한 경계 계산은 이미지/컨테이너 실제 크기 측정이 필요하지만,
  //  이 정도로도 UX가 좋아요.)
  const maxPan = 800 * (zoom - 1);  // zoom이 클수록 더 많이 이동 허용
  const limit = Math.max(0, maxPan);

  tx = Math.max(-limit, Math.min(limit, tx));
  ty = Math.max(-limit, Math.min(limit, ty));
}

// 휠 줌
document.getElementById("lightbox").addEventListener("wheel", (e) => {
  const lightbox = document.getElementById("lightbox");
  if (lightbox.style.display !== "flex") return;

  e.preventDefault();

  const delta = Math.sign(e.deltaY);
  const prevZoom = zoom;

  zoom = zoom * (delta > 0 ? (1 - ZOOM_STEP) : (1 + ZOOM_STEP));
  zoom = Math.min(ZOOM_MAX, Math.max(ZOOM_MIN, zoom));

  // zoom이 1로 돌아오면 pan도 리셋하면 깔끔
  if (zoom === 1) { tx = 0; ty = 0; }

  // 너무 과한 pan 방지
  if (zoom !== prevZoom) clampPan();
  applyTransform();
}, { passive: false });

// 드래그 시작/이동/끝 (Pointer Events: 마우스/트랙패드 모두)
const inner = document.getElementById("lightbox-inner");

inner.addEventListener("pointerdown", (e) => {
  const lightbox = document.getElementById("lightbox");
  if (lightbox.style.display !== "flex") return;

  // zoom=1일 때는 굳이 드래그 이동하지 않게 해도 됨(원하면 제거 가능)
  if (zoom === 1) return;

  isDragging = true;
  inner.classList.add("dragging");
  inner.setPointerCapture(e.pointerId);

  startX = e.clientX;
  startY = e.clientY;
  startTx = tx;
  startTy = ty;
});

inner.addEventListener("pointermove", (e) => {
  if (!isDragging) return;

  const dx = e.clientX - startX;
  const dy = e.clientY - startY;

  tx = startTx + dx;
  ty = startTy + dy;

  clampPan();
  applyTransform();
});

inner.addEventListener("pointerup", () => {
  isDragging = false;
  inner.classList.remove("dragging");
});

inner.addEventListener("pointercancel", () => {
  isDragging = false;
  inner.classList.remove("dragging");
});

// ESC로 닫기
document.addEventListener("keydown", (e) => {
  if (e.key === "Escape") closeLightbox();
});
</script>
