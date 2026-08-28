# Mara Guard AI Intelligence Layer: Technical Specifications

The core intelligence layer of Mara Guard relies on a custom-trained, edge-optimized **Ultralytics YOLOv8 (You Only Look Once)** computer vision model. This architecture handles real-time single-pass object detection, multi-object tracking, and automated threat density count categorization directly on field hardware.

---

## Section 1: Development Sandbox & Environment Baseline

### Engineering Team
* **Rose Wanjiru Muragu**
* **Ineza Lira Gabriella**
* **Esther Kazungu**
* **Prudence Ndolo**



<div class="custom-card-container">
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Shared Storage Mounting Protocol</h3>
    <p style="color: #42281A !important;">To persist neural weights beyond temporary container lifecycles, the team established a secure runtime mount to shared network storage pools:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-python" style="color: #42281A !important; background: transparent !important;">from google.colab import drive
drive.mount('/content/drive')</code></pre>
  </div>
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">System Verification Signature</h3>
    <p style="color: #42281A !important;">Deterministic baseline testing confirms the underlying tooling allocations before parameter compilation starts:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-text" style="color: #42281A !important; background: transparent !important;">Ultralytics 8.4.127  Python-3.13.15 torch-2.11.0+cu120 CUDA:0 (Tesla T4, 14913MiB)
Setup complete  (12 CPUs, 12.7 GB RAM, 47.2/112.6 GB disk)</code></pre>
  </div>
</div>

---

## Section 2: Data Engineering & Pipeline Sanitization

### Ingestion Source
The annotated computer vision corpus was pulled directly from our group's cloud repository workspace using the Roboflow native platform wrapper API.

<div class="custom-card-container">
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Dataset Ingestion Profile</h3>
    <p style="color: #42281A !important;">Executes structural platform authentication and target archive assembly pull requests:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-python" style="color: #42281A !important; background: transparent !important;">from roboflow import Roboflow
rf = Roboflow(api_key="HjIvvD9co08AYBKA6SUd")
project = rf.workspace("muragu-wanjiru").project("lion-a0vv0-s4mdt")
version = project.version(1)
dataset = version.download("yolov8")</code></pre>
  </div>
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Processing Pipeline Rules</h3>
    <p style="color: #42281A !important;">Core optimization and cleanup triggers executed on data sequence streams:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-text" style="color: #42281A !important; background: transparent !important;">[Local Lookup Generation] -> Created lookup mapping: /content/Lion-1/valid/labels.cache
           |
[Token De-duplication]   -> Sanitized sequence logs: 1 duplicate labels removed
           |
[Geometric Alignment]    -> Corrected imbalance: dropping segments to match bounding assets</code></pre>
  </div>
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Geometry Rectification Warning</h3>
    <p style="color: #42281A !important;">The framework overrides segmentation polygon imbalances to preserve node calculation speeds:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-text" style="color: #42281A !important; background: transparent !important;">WARNING  A box and segment counts should be equal, but got len(segments) = 342, len(boxes) = 446.</code></pre>
    <p style="color: #42281A !important;"><em>Action:</em> Prioritizes rectangular 2D object-bounding detection boxes (<code style="color: #CD8151 !important; background: transparent !important;">len(boxes) = 446</code>).</p>
  </div>
</div>

### Pixel-Level Augmentation Configurations
To track focal points under pitch-black midnight wilderness constraints, the data pipeline runs custom Albumentations:
Blur(p=0.01, blur_limit=(3, 7)) MedianBlur: Replicates physical impact movement tracking artifacts on a fence node.
CAHE(p=0.01, clip_limit=(1.0, 4.0)): Normalizes dynamic contrast fields across volatile wilderness shadows.

---

## Section 3: Architecture Scale & Network Profile

The standard multi-class target baseline was stripped down to optimize channel throughput:

Overriding model.yaml nc=80 with nc=1

By compressing standard classification matrices from 80 generic classes to exactly 1 target class (class: lion), the network minimizes runtime overhead.

### Structural Complexity Specs
 **Structural Topology Layers:** 130
 **Parametric Footprint Scale:** 3,011,043 parameters
 **Active Gradient Tracking Channels:** 3,011,027 elements
 **Matrix Computation Bandwidth:** 8.2 GFLOPs

---

## Section 4: Training Execution Loop

<div class="custom-card-container">
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">CLI Training Invocation</h3>
    <p style="color: #42281A !important;">Terminal processing loop assigning hardware metrics and targeting specific ecosystem parameter files:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-bash" style="color: #42281A !important; background: transparent !important;">!yolo detect train model=yolov8n.pt data=/content/Lion-1/data.yaml epochs=5 imgsz=640 device=0</code></pre>
  </div>
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Epoch Optimization History Log</h3>
    <p style="color: #42281A !important;">Parameter stabilization track mapping classification and object loss ceilings over time:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-text" style="color: #42281A !important; background: transparent !important;">Epoch 1/5 -> [Cls Loss Score: 0.3042] -> [Track Count: 1 Instance Checked]
Epoch 2/5 -> [Cls Loss Score: 0.6670] -> [Track Count: 8.3980 Instances]
Epoch 3/5 -> [Cls Loss Score: 0.6100] -> [Track Count: 8.0180 Instances]
Epoch 4/5 -> [Cls Loss Score: 0.7550] -> [Track Count: 8.6080 Instances]
Epoch 5/5 -> [Cls Loss Score: 0.8840] -> [Track Count: 8.7750 Instances]</code></pre>
    <p style="color: #42281A !important;"><em>Duration Metric:</em> 5 epochs completed in 0.012 hours (43.2 seconds).</p>
  </div>
</div>

### Optimization Hyperparameters
 model=yolov8n.pt: Selected Nano topology variant to minimize latency constraints on field edge hardware.
 imgsz=640: Constrains inputs to symmetric 640x640 pixel grids to guarantee continuous real-time execution frames.
 Optimizer=AdamW: Bound to a base learning floor of lr0=0.002 with a momentum constraint ceiling of 0.9.

---

## Section 5: Compilation Overrides & Edge Adaptation

<div class="custom-card-container">
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Edge Strip Pass Response</h3>
    <p style="color: #42281A !important;">Post-training automation routine stripping extra logging structures to save RAM storage channels:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-text" style="color: #42281A !important; background: transparent !important;">Optimizer stripped from /content/runs/detect/train/weights/best.pt, 6.2MB</code></pre>
  </div>
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Footprint Minimization</h3>
    <p style="color: #42281A !important;">Gradient tracking calculations are fully stripped, dropping total deployment scale to <strong>exactly 6.2 Megabytes</strong> for execution inside Raspberry Pi 5 edge nodes.</p>
  </div>
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Automatic Mixed Precision</h3>
    <p style="color: #42281A !important;">By compiling with <code style="color: #CD8151 !important; background: transparent !important;">AMP=True</code>, arithmetic loops fold into FP16 and FP32 clusters, doubling hardware processing throughput rules without dropping precision bounds.</p>
  </div>
</div>

---
  ### Environment Context
 **Interactive Notebook:** [Google Colab Workspace](https://colab.research.google.com/drive/149ljCCZKRykwVr4Lam5p_pIYwD-ci-Ef#scrollTo=rqwiwdzw9l2b)
 
## Section 6: Empirical Metrics & Validation Logs

<div class="custom-card-container">
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Inference Pipeline Initialization</h3>
    <p style="color: #42281A !important;">Invokes verified analytical passes across raw threat directory boundaries:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-python" style="color: #42281A !important; background: transparent !important;">model = YOLO('runs/detect/train/weights/best.pt')
results = model.predict(source='/content/Lion-1/valid/images', save=True, conf=0.25)</code></pre>
  </div>
  <div class="custom-card" style="background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Batch Evaluation History Ledger</h3>
    <p style="color: #42281A !important;">Raw runtime tracking extracts mapping geographic image sizes to threat count latency counts:</p>
    <pre style="background-color: #FFFFFF !important; border: 1px solid #D4C5BD !important; padding: 12px; border-radius: 8px;"><code class="language-text" style="color: #42281A !important; background: transparent !important;">[image 01/81] 480 x 640 px   2 Lions Verified     6.1 ms Latency
[image 14/81] 384 x 640 px   3 Lions Verified     6.9 ms Latency
[image 17/81] 384 x 640 px   6 Lions Verified     6.0 ms Latency
[image 51/81] 640 x 640 px   2 Lions Verified     9.1 ms Latency
[image 58/81] 640 x 640 px   2 Lions Verified     8.0 ms Latency
[image 73/81] 640 x 640 px   2 Lions Verified     7.4 ms Latency
[image 81/81] 640 x 640 px   2 Lions Verified     9.6 ms Latency</code></pre>
  </div>
</div>

<div class="custom-card-container">
  <div class="custom-card" style="flex: 1 1 100% !important; background-color: #FFFFFF !important; border: 1px solid #CD8151 !important;">
    <h3 style="color: #2D1A10 !important;">Validation Dataset Benchmarks</h3>
    <p style="color: #42281A !important;">Evaluation passes executed against 81 reference validation images mapping 102 threat instances yielded the following structural accuracy rates:</p>
    <table style="width: 100%; border-collapse: collapse; margin-top: 12px;">
      <thead>
        <tr style="border-bottom: 2px solid #FFFFFF; text-align: left;">
          <th style="color:#FFFFFF !important; padding: 8px;">Tracking Parameter</th>
          <th style="color: #FFFFFF !important; padding: 8px;">Technical Metric Name</th>
          <th style="color: #FFFFFF!important; padding: 8px;">Realized Operational Score</th>
          <th style="color: #FFFFFF !important; padding: 8px;">Performance Output</th>
        </tr>
      </thead>
      <tbody>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #FFFFFF !important; padding: 8px;"><strong>P</strong></td>
          <td style="color: #FFFFFF !important; padding: 8px;">Box Precision Metric</td>
          <td style="color: #FFFFFF !important; padding: 8px;"><code style="color: #CD8151 !important; background: transparent !important;">0.865</code></td>
          <td style="color:#FFFFFF !important; padding: 8px;">86.5% Accuracy</td>
        </tr>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #FFFFFF !important; padding: 8px;"><strong>R</strong></td>
          <td style="color: #FFFFFF !important; padding: 8px;">Recall Performance Value</td>
          <td style="color: #FFFFFF !important; padding: 8px;"><code style="color: #CD8151 !important; background: transparent !important;">0.775</code></td>
          <td style="color: #FFFFFF !important; padding: 8px;">77.5% True Positive Catch Rate</td>
        </tr>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #FFFFFF !important; padding: 8px;"><strong>mAP@50</strong></td>
          <td style="color:#FFFFFF !important; padding: 8px;">Mean Average Precision Threshold</td>
          <td style="color: #FFFFFF !important; padding: 8px;"><code style="color: #CD8151 !important; background: transparent !important;">0.884</code></td>
          <td style="color: #FFFFFF !important; padding: 8px;">88.4% Intersection Benchmark</td>
        </tr>
        <tr style="border-bottom: 1px solid #D4C5BD;">
          <td style="color: #FFFFFF!important; padding: 8px;"><strong>mAP@50-95</strong></td>
          <td style="color: #FFFFFF !important; padding: 8px;">Deep Positional Spatial Tracking</td>
          <td style="color: #FFFFFF !important; padding: 8px;"><code style="color: #CD8151 !important; background: transparent !important;">0.513</code></td>
          <td style="color: #FFFFFF !important; padding: 8px;">51.3% Complex Geometry Scale</td>
        </tr>
      </tbody>
    </table>
  </div>

</div>

