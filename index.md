---
layout: home
title: "Soyeon Park"
---

<link rel="stylesheet" href="/assets/css/custom.css">

##### Hi all 👋 I'm Soyeon Park, a Master’s student in Statistics at Northwestern University.
##### Previously I was a Staff Engineer in Evaluation & Analysis Team at <span class="blue-text"><a href="https://semiconductor.samsung.com/">Samsung Electronics</a></span>, specializing in data analysis, automation, and machine learning applications in semiconductor manufacturing.
##### Currently expanding my expertise in statistics and data science with strong interest in robust modeling under limited data. My goal is to contribute to scalable, trustworthy models that address real-world challenges in technology and industry.





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
    <span class="project-subtitle">Using statistical and machine learning models to support budgeting and resource allocation</span>
    <br><br>
    <img src="/assets/images/project_capacity.png"
    alt="Capacity Forecasting"
    class="project-image"
    onclick="openLightbox(this)">
  </div>


  <div class="project-card">
    <strong style="font-size: 1.05rem;">Transfer Learning Evaluation for Process Monitoring</strong><br>
    <span class="project-subtitle">Adaptive Predictive Modeling for Dynamic Process Monitoring</span>
    <br><br>
    <img src="/assets/images/project_transfer.png"
    alt="Transfer Learning Project"
    class="project-image"
    onclick="openLightbox(this)">
  </div>


  <div class="project-card">
    <strong style="font-size: 1.05rem;">End-to-End Workflow Automation for Quality Analytics</strong><br>
    <span class="project-subtitle">ETL + feature scoring + dashboards to reduce manual work and downtime</span>
    <br><br>
    <img src="/assets/images/project_automation.png"
    alt="Workflow Automation Project"
    class="project-image"
    onclick="openLightbox(this)">
  </div>


  <div class="project-card">
    <strong style="font-size: 1.05rem;">Super-Resolution Imaging to Increase Inspection Throughput</strong><br>
    <span class="project-subtitle">Computer vision pipeline to reduce capture time and avoid equipment spend</span>
    <br><br>
    <img src="/assets/images/project_sr.png"
    alt="Super Resolution Project"
    class="project-image"
    onclick="openLightbox(this)">
  </div>

</div>

<div id="lightbox" onclick="closeLightbox()">
  <img id="lightbox-img" alt="">
</div>


<script>
let zoom = 1;
const ZOOM_MIN = 1;
const ZOOM_MAX = 4;
const ZOOM_STEP = 0.12;

function openLightbox(img) {
  const lightbox = document.getElementById("lightbox");
  const lightboxImg = document.getElementById("lightbox-img");

  lightboxImg.src = img.src;
  zoom = 1;
  lightboxImg.style.transform = `scale(${zoom})`;

  lightbox.style.display = "flex";
  document.body.style.overflow = "hidden"; // 배경 스크롤 방지
}

document.addEventListener("keydown", e => {
  if (e.key === "Escape") closeLightbox();
});

function closeLightbox() {
  document.getElementById("lightbox").style.display = "none";
  document.body.style.overflow = ""; // 원복
}

document.getElementById("lightbox").addEventListener("wheel", (e) => {
  // 휠로 확대/축소, 페이지 스크롤 막기
  e.preventDefault();

  const img = document.getElementById("lightbox-img");
  const delta = Math.sign(e.deltaY);

  // deltaY > 0 : 아래로 스크롤(축소), deltaY < 0 : 확대
  zoom = zoom * (delta > 0 ? (1 - ZOOM_STEP) : (1 + ZOOM_STEP));
  zoom = Math.min(ZOOM_MAX, Math.max(ZOOM_MIN, zoom));

  img.style.transform = `scale(${zoom})`;
}, { passive: false });
</script>
