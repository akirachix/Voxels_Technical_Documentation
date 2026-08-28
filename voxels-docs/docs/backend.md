<div class="api-page">

<div class="api-hero">
  <h1>Backend</h1>
  <p class="hero-subtitle">Mara Guard API - FastAPI backend for Voxels wildlife monitoring system.</p>
  <div class="tech-badges">
    <span class="tech-badge">FastAPI</span>
    <span class="tech-badge">PostgreSQL</span>
    <span class="tech-badge">SQLAlchemy 2.0</span>
    <span class="tech-badge">JWT</span>
    <span class="tech-badge">Redis</span>
    <span class="tech-badge">Alembic</span>
    <span class="tech-badge">Python 3.12</span>
  </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  if (typeof mermaid !== 'undefined') {
    mermaid.initialize({
      startOnLoad: true,
      theme: 'dark',
      themeVariables: {
        primaryColor: '#2D1A10',
        primaryTextColor: '#FFFFFF',
        primaryBorderColor: '#CD8151',
        lineColor: '#CD8151',
        secondaryColor: '#3D2A1E',
        tertiaryColor: '#1a0f0a',
        background: '#1a0f0a',
        mainBkg: '#2D1A10',
        nodeBorder: '#CD8151',
        clusterBkg: '#3D2A1E',
        titleColor: '#FFFFFF',
        edgeLabelBackground: '#2D1A10',
        fontFamily: 'Poppins, Segoe UI, Arial, sans-serif',
        relationshipLabelColor: '#CD8151',
        relationshipLineColor: '#CD8151'
      },
      er: {
        layoutDirection: 'LR',
        minEntityWidth: 180,
        minEntityHeight: 110,
        entityPadding: 25,
        fontSize: 15
      },
      flowchart: {
        useMaxWidth: true,
        htmlLabels: true,
        curve: 'basis'
      }
    });
  }
});
</script>
<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  window.mermaid = mermaid;
  mermaid.initialize({
    startOnLoad: true,
    theme: 'dark',
    themeVariables: {
      primaryColor: '#2D1A10',
      primaryTextColor: '#FFFFFF',
      primaryBorderColor: '#CD8151',
      lineColor: '#CD8151',
      secondaryColor: '#3D2A1E',
      tertiaryColor: '#1a0f0a',
      background: '#1a0f0a',
      mainBkg: '#2D1A10',
      nodeBorder: '#CD8151',
      clusterBkg: '#3D2A1E',
      titleColor: '#FFFFFF',
      edgeLabelBackground: '#2D1A10',
      fontFamily: 'Poppins, Segoe UI, Arial, sans-serif',
      relationshipLabelColor: '#CD8151',
      relationshipLineColor: '#CD8151'
    },
    er: {
      layoutDirection: 'LR',
      minEntityWidth: 180,
      minEntityHeight: 110,
      entityPadding: 25,
      fontSize: 15
    },
    flowchart: {
      useMaxWidth: true,
      htmlLabels: true,
      curve: 'basis'
    }
  });
</script>
</div>

<div class="api-section">

<div class="section-title">API Overview</div>

<h3 class="subsection-title">Framework</h3>
<p>FastAPI</p>

<h3 class="subsection-title">Version</h3>
<p>v1</p>

<h3 class="subsection-title">Base Path</h3>
<p>/</p>

</div>

<div class="api-section">

<div class="section-title">Hosted API</div>

<h3 class="subsection-title">Production URL</h3>
<p>https://maraguard-3686f239afe8.herokuapp.com</p>

<h3 class="subsection-title">Documentation</h3>

<ul>
  <li><a href="https://maraguard-3686f239afe8.herokuapp.com/docs" target="_blank">Swagger UI</a></li>
  <li><a href="https://maraguard-3686f239afe8.herokuapp.com/redoc" target="_blank">ReDoc</a></li>
</ul>

</div>

<div class="api-section">

<div class="section-title">Prerequisites</div>

<h3 class="subsection-title">Requirements</h3>
<p>Python 3.12+, PostgreSQL, Redis (optional).</p>

</div>

<div class="api-section">

<div class="section-title">Setup and Installation</div>

<h3 class="subsection-title">Step 1</h3>
<p>Clone repo and cd into project</p>

<h3 class="subsection-title">Step 2</h3>
<p>python -m venv env && source env/bin/activate</p>

<h3 class="subsection-title">Step 3</h3>
<p>pip install -r requirements.txt</p>

<h3 class="subsection-title">Step 4</h3>
<p>Create .env with DATABASE_URL, SECRET_KEY, REDIS_URL, MAIL_*</p>

<h3 class="subsection-title">Step 5</h3>
<p>alembic upgrade head</p>

<h3 class="subsection-title">Step 6</h3>
<p>python main.py</p>

</div>

<div class="api-section">

<div class="section-title">Architecture Layers</div>

<h3 class="subsection-title">Router</h3>
<p>API routes and endpoint definitions</p>

<h3 class="subsection-title">Schema</h3>
<p>Pydantic request/response validation</p>

<h3 class="subsection-title">Service</h3>
<p>Business logic and orchestration</p>

<h3 class="subsection-title">Repository</h3>
<p>Database access and queries</p>

</div>

<div class="api-section">

<div class="section-title">API Conventions</div>

<h3 class="subsection-title">Base URL</h3>
<p>https://maraguard-3686f239afe8.herokuapp.com</p>

<h3 class="subsection-title">Authentication</h3>
<p>JWT Bearer token in Authorization header</p>

<h3 class="subsection-title">Status Codes</h3>
<p>200, 201, 400, 401, 404, 429, 500</p>

</div>

<div class="api-section">

<div class="section-title">Endpoint Categories</div>

<h3 class="subsection-title">Authentication & User Management</h3>

<div class="endpoint-row">
  <span class="method method-post">POST</span>
  <span class="path">/rangers/register</span>
  <span class="desc">Register a new ranger</span>
</div>

<div class="endpoint-row">
  <span class="method method-post">POST</span>
  <span class="path">/rangers/login</span>
  <span class="desc">Login, returns JWT token</span>
</div>

<div class="endpoint-row">
  <span class="method method-get">GET</span>
  <span class="path">/rangers/me</span>
  <span class="desc">Get current ranger profile</span>
</div>

<div class="endpoint-row">
  <span class="method method-get">GET</span>
  <span class="path">/rangers/</span>
  <span class="desc">List all rangers (admin)</span>
</div>

<h3 class="subsection-title">Password Management</h3>

<div class="endpoint-row">
  <span class="method method-post">POST</span>
  <span class="path">/rangers/forgot-password</span>
  <span class="desc">Initiate password reset</span>
</div>

<div class="endpoint-row">
  <span class="method method-post">POST</span>
  <span class="path">/rangers/verify-reset-code</span>
  <span class="desc">Verify reset code</span>
</div>

<div class="endpoint-row">
  <span class="method method-post">POST</span>
  <span class="path">/rangers/reset-password</span>
  <span class="desc">Reset password</span>
</div>

<h3 class="subsection-title">Detection Management</h3>

<div class="endpoint-row">
  <span class="method method-post">POST</span>
  <span class="path">/detection</span>
  <span class="desc">Log a new lion detection</span>
</div>

<div class="endpoint-row">
  <span class="method method-get">GET</span>
  <span class="path">/detection</span>
  <span class="desc">List detections (filter by date)</span>
</div>

<h3 class="subsection-title">Telemetry Management</h3>

<div class="endpoint-row">
  <span class="method method-post">POST</span>
  <span class="path">/telemetry/</span>
  <span class="desc">Create a new telemetry log</span>
</div>

<div class="endpoint-row">
  <span class="method method-get">GET</span>
  <span class="path">/telemetry/</span>
  <span class="desc">Read all telemetry logs</span>
</div>

<div class="endpoint-row">
  <span class="method method-patch">PATCH</span>
  <span class="path">/telemetry/{log_id}</span>
  <span class="desc">Update a telemetry log</span>
</div>

<div class="endpoint-row">
  <span class="method method-delete">DELETE</span>
  <span class="path">/telemetry/{log_id}</span>
  <span class="desc">Delete a telemetry log</span>
</div>

</div>

<div class="api-section">

<div class="section-title">Data Models</div>

<h3 class="subsection-title">Database Schema</h3>

<p>PostgreSQL database with SQLAlchemy 2.0 ORM and Alembic migrations.</p>

<div class="erd-wrapper">
<div class="erd-glow"></div>
<div class="erd-container">

```mermaid
erDiagram
    RANGERS ||--o{ TELEMETRY_LOGS : "has"
    TELEMETRY_LOGS ||--o{ DETECTIONS : "contains"

    RANGERS {
        int ranger_id PK
        string first_name
        string last_name
        string email
        string password_hash
    }

    TELEMETRY_LOGS {
        string log_id PK
        string ranger_id FK
        datetime datetime
        decimal battery_level
    }

    DETECTIONS {
        string detection_id PK
        string log_id FK
        datetime time_captured
        decimal confidence_score
        int lion_count
    }
```

</div>
</div>

<h3 class="subsection-title">Ranger</h3>

<div class="styled-table-wrapper">
<table class="styled-table">
  <thead>
    <tr>
      <th>Field</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>ranger_id</td>
      <td>Integer</td>
      <td>Primary key</td>
    </tr>
    <tr>
      <td>first_name</td>
      <td>String(100)</td>
      <td>Ranger's first name</td>
    </tr>
    <tr>
      <td>last_name</td>
      <td>String(100)</td>
      <td>Ranger's last name</td>
    </tr>
    <tr>
      <td>email</td>
      <td>String(100)</td>
      <td>Unique email address</td>
    </tr>
    <tr>
      <td>password_hash</td>
      <td>String(255)</td>
      <td>Bcrypt hashed password</td>
    </tr>
  </tbody>
</table>
</div>

<h3 class="subsection-title">Detection</h3>

<div class="styled-table-wrapper">
<table class="styled-table">
  <thead>
    <tr>
      <th>Field</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>detection_id</td>
      <td>String(36)</td>
      <td>UUID primary key</td>
    </tr>
    <tr>
      <td>log_id</td>
      <td>String(36)</td>
      <td>Associated telemetry log</td>
    </tr>
    <tr>
      <td>time_captured</td>
      <td>DateTime</td>
      <td>Timestamp of detection</td>
    </tr>
    <tr>
      <td>confidence_score</td>
      <td>Numeric(3,2)</td>
      <td>AI confidence (0.00 - 1.00)</td>
    </tr>
    <tr>
      <td>lion_count</td>
      <td>Integer</td>
      <td>Number of lions detected</td>
    </tr>
  </tbody>
</table>
</div>

<h3 class="subsection-title">Telemetry Log</h3>

<div class="styled-table-wrapper">
<table class="styled-table">
  <thead>
    <tr>
      <th>Field</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>log_id</td>
      <td>String(36)</td>
      <td>UUID primary key</td>
    </tr>
    <tr>
      <td>ranger_id</td>
      <td>String(36)</td>
      <td>Ranger who created the log</td>
    </tr>
    <tr>
      <td>datetime</td>
      <td>DateTime</td>
      <td>Log timestamp</td>
    </tr>
    <tr>
      <td>battery_level</td>
      <td>Numeric(10,2)</td>
      <td>Battery percentage (0 - 100)</td>
    </tr>
  </tbody>
</table>
</div>

</div>

<div class="api-section">

<div class="section-title">Testing and QA</div>

<h3 class="subsection-title">Framework</h3>
<p>pytest for unit tests.</p>

<h3 class="subsection-title">Run Tests</h3>

```bash
pytest
```

</div>

<div class="api-section">

<div class="section-title">Code Standards</div>

<h3 class="subsection-title">Naming</h3>
<p>snake_case for variables/functions/files, PascalCase for classes/models.</p>

<h3 class="subsection-title">Structure</h3>
<p>routers, schemas, services, repositories in separate files.</p>

<h3 class="subsection-title">Commits</h3>
<p>conventional commits (feat, fix, docs, etc.)</p>

</div>

<div class="api-section">

<div class="section-title">Deployment</div>

<h3 class="subsection-title">Platform</h3>
<p>Heroku (Staging & Production)</p>

<h3 class="subsection-title">Branch</h3>
<p>Deploy from main</p>

<h3 class="subsection-title">Environment Variables</h3>
<p>Managed in Heroku dashboard.</p>

<h3 class="subsection-title">Scaling</h3>
<p>Auto-scaling via Heroku dynos.</p>

<h3 class="subsection-title">Rollback</h3>
<p>Rollback to previous release via Heroku dashboard.</p>

</div>

</div>

</div>
