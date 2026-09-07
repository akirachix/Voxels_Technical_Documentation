# Welcome to Mara Guard

<div class="carousel" id="maraguard-hero-slideshow">
  <div class="carousel-slide active">
    <img src="images/logo.png" alt="Mara Guard Logo" class="logo" style="max-width: 180px; height: auto; margin: 0 auto 1.5em auto;">
    <h2>Coexistence. Protection. Innovation.</h2>
    <p>An autonomous, edge-AI conflict mitigation network safeguarding livestock and lions.</p>
  </div>

  <div class="carousel-slide">
    <img src="images/dashboard.png" alt="Ranger Operations Dashboard" class="platform-img">
    <h2>Incident Alerts. Telemetry. Analytics.</h2>
    <p>Empowering field rangers and Maasai pastoralists with proactive regional tracking tools.</p>
  </div>

  <div class="carousel-slide">
    <img src="images/test.png" alt="Embedded YOLOv8 Verification" class="platform-img">
    <h2>On-Board Neural Network Verification</h2>
    <p>Solar-powered edge nodes running local machine vision scripts in any weather state.</p>
  </div>

  <div class="carousel-dots">
    <span class="carousel-dot active" data-slide="0"></span>
    <span class="carousel-dot" data-slide="1"></span>
    <span class="carousel-dot" data-slide="2"></span>
  </div>
</div>

<div class="button-container">
  <a href="https://voxels-informational-website.vercel.app/" class="md-button">Informational Website</a>
  <a href="getting-started/" class="md-button">See what's next</a>
</div>

---

<div style="text-align: center; font-size: 1.18rem; color: #FFFFFF; margin: 2em 0; line-height: 1.7;">
  <strong>Mara Guard</strong> is an edge-AI ecosystem designed by the Voxels engineering team,<br>
  connecting standalone solar telemetry nodes with localized YOLOv8 neural network matching loops, streamlining automated threat interception and<br> enabling wildlife rangers to track active intrusions and monitor device health metrics via point-to-point radio linkages thereby enhancing community-led conservation.
 </div>

---
## Why Mara Guard?

<div class="custom-card-container">

<div class="custom-card">
  <h3>Edge-AI Threat Classification</h3>
  <p>Executes optimized convolutional inference maps locally on an integrated Raspberry Pi 5 host processor, achieving real-time predator verification within 12.3ms of signal ingestion.</p>
</div>

<div class="custom-card">
  <h3>All-Weather Microwave Radar</h3>
  <p>Employs standalone radar tracking arrays to monitor boundary perimeters up to 6 meters deep, completely filtering out adverse field elements like heavy rain, dust storms, dense fog, or midnight thermal distortion.</p>
</div>

<div class="custom-card">
  <h3>Layered Autonomous Countermeasures</h3>
  <p>Triggers dual startle-defense circuits instantly upon threat validation—switching on high-lumen spotlights to disorient nocturnal tracking vision while blasting high-decibel horns continuously until all lions clear the zone.</p>
</div>

<div class="custom-card">
  <h3>Long-Range Radio Telemetry (LoRa)</h3>
  <p>Bypasses commercial cellular infrastructure dependencies by packaging active incident logs into compact binary streams, broadcasting them across isolated territories using point-to-point LoRa radio link arrays.</p>
</div>

<div class="custom-card">
  <h3>Empirical Precision & False-Alarm Rejection</h3>
  <p>Enforces a strict 60% validation threshold via anchor-free neural detection heads, ensuring the node automatically ignores non-threatening movement like wind-blown brush, domestic herding dogs, or livestock cattle.</p>
</div>

<div class="custom-card">
  <h3>Real-Time Ranger Analytics Hub</h3>
  <p>Funnels incoming gateway telemetry over an automated MQTT broker path to populate custom web management panels with real-time intrusion lists, historic trend timelines, predator densities, and INA219 battery voltage records.</p>
</div>

</div>


---


---

<div class="mission-banner">
  <strong>Our Mission:</strong> <em>Mitigate escalating human-wildlife conflict within the Maasai Mara Reserve ecosystem.<br>
  Replace dangerous field blindspots with secure, trackable edge-intelligence arrays built to protect communal assets and preserve vulnerable lion prides.</em>
</div>

---

> _Learn more about Mara Guard on our [Informational Portal](https://voxels-informational-website.vercel.app/)._  
> _Ready to build the edge node hardware stack? [Jump to the Getting Started Guide](getting-started.md)!_

<script>
document.addEventListener('DOMContentLoaded', function() {
  const slides = document.querySelectorAll('.carousel-slide');
  const dots = document.querySelectorAll('.carousel-dot');
  let current = 0;

  function showSlide(index) {
    slides.forEach((slide, i) => {
      slide.classList.toggle('active', i === index);
    });
    dots.forEach((dot, i) => {
      dot.classList.toggle('active', i === index);
    });
    current = index;
  }

  dots.forEach((dot, i) => {
    dot.addEventListener('click', () => showSlide(i));
  });

  setInterval(() => {
    showSlide((current + 1) % slides.length);
  }, 6000);

  showSlide(0);
});
</script>
