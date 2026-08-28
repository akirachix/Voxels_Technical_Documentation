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

<p>Framework: FastAPI</p>
<p>Version: v1</p>
<p>Base Path: /</p>

</div>

<div class="api-section">

<div class="section-title">Hosted API</div>

<p>Production URL: https://maraguard-3686f239afe8.herokuapp.com</p>

<ul>
  <li><a href="https://maraguard-3686f239afe8.herokuapp.com/docs" target="_blank">Swagger UI</a></li>
  <li><a href="https://maraguard-3686f239afe8.herokuapp.com/redoc" target="_blank">ReDoc</a></li>
</ul>

</div>

<div class="api-section">

<div class="section-title">Prerequisites</div>

<p>Python 3.12+, PostgreSQL, Redis (optional).</p>

</div>

<div class="api-section">

<div class="section-title">Setup and Installation</div>

<p>1. Clone repo and cd into project</p>
<p>2. python -m venv env && source env/bin/activate</p>
<p>3. pip install -r requirements.txt</p>
<p>4. Create .env with DATABASE_URL, SECRET_KEY, REDIS_URL, MAIL_*</p>
<p>5. alembic upgrade head</p>
<p>6. python main.py</p>

</div>

<div class="api-section">

<div class="section-title">Architecture Layers</div>

<p>Router: API routes and endpoint definitions</p>
<p>Schema: Pydantic request/response validation</p>
<p>Service: Business logic and orchestration</p>
<p>Repository: Database access and queries</p>

</div>

<div class="api-section">

<div class="section-title">API Conventions</div>

<p>Base URL: https://maraguard-3686f239afe8.herokuapp.com</p>

<p>Authentication: JWT Bearer token in Authorization header</p>

<p>Status Codes: 200, 201, 400, 401, 404, 429, 500</p>

</div>

<div class="api-section">

<div class="section-title">Endpoint Categories</div>

<h3 class="subsection-title">Authentication & User Management</h3>

<p>POST /rangers/register - Register a new ranger</p>
<p>POST /rangers/login - Login, returns JWT token</p>
<p>GET /rangers/me - Get current ranger profile</p>
<p>GET /rangers/ - List all rangers (admin)</p>

<h3 class="subsection-title">Password Management</h3>

<p>POST /rangers/forgot-password - Initiate password reset</p>
<p>POST /rangers/verify-reset-code - Verify reset code</p>
<p>POST /rangers/reset-password - Reset password</p>

<h3 class="subsection-title">Detection Management</h3>

<p>POST /detection - Log a new lion detection</p>
<p>GET /detection - List detections (filter by date)</p>

<h3 class="subsection-title">Telemetry Management</h3>

<p>POST /telemetry/ - Create a new telemetry log</p>
<p>GET /telemetry/ - Read all telemetry logs</p>
<p>PATCH /telemetry/{log_id} - Update a telemetry log</p>
<p>DELETE /telemetry/{log_id} - Delete a telemetry log</p>

</div>

<div class="api-section">

<div class="section-title">Data Models</div>

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

<p>pytest for unit tests.</p>

<p>Run tests:</p>

```bash
pytest
```

</div>

<div class="api-section">

<div class="section-title">Code Standards</div>

<p>Naming: snake_case for variables/functions/files, PascalCase for classes/models.</p>

<p>Structure: routers, schemas, services, repositories in separate files.</p>

<p>Commits: conventional commits (feat, fix, docs, etc.)</p>

</div>

<div class="api-section">

<div class="section-title">Deployment</div>

<p>Platform: Heroku (Staging & Production)</p>

<p>Branch: Deploy from main</p>

<p>Environment variables managed in Heroku dashboard.</p>

<p>Auto-scaling via Heroku dynos.</p>

<p>Rollback to previous release via Heroku dashboard.</p>

</div>

</div>
