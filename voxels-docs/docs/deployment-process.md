## 1. Backend Deployment

The [Voxels Backend repository](https://github.com/akirachix/Voxels_Backend) contains the backend API for Mara Guard. It is built using **Python, FastAPI, and PostgreSQL**. The backend receives and provides system data for the dashboard and other parts of the Mara Guard system.

---

### 1.1 Why the Backend Is Deployed

The backend is deployed so that Mara Guard applications can communicate with the system remotely.

It provides services for:

* Ranger authentication
* Lion detection information
* Intrusion records
* Device and battery information
* Database operations
* Communication between system components

The hosted API can be accessed through the [Mara Guard API Documentation](https://maraguard-3686f239afe8.herokuapp.com/docs).

---

### 1.2 Prerequisites

Before setting up or deploying the backend, make sure you have:

* **Python 3.10 or higher**
* **Git**
* **PostgreSQL**
* A **Heroku account**
* Access to the [Voxels Backend repository](https://github.com/akirachix/Voxels_Backend)

Clone the repository:

```bash
git clone https://github.com/akirachix/Voxels_Backend.git
cd Voxels_Backend
```

Create and activate a virtual environment:

```bash
python3 -m venv env
source env/bin/activate
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

---

### 1.3 Environment Configuration

The backend uses environment variables for configuration and sensitive information.

Create a `.env` file in the project root:

```env
PORT=5000
DATABASE_URL=postgresql://user:password@localhost:5432/maraguard
JWT_SECRET_KEY=your_secret_key
MQTT_BROKER_USER=your_mqtt_username
MQTT_BROKER_PASSWORD=your_mqtt_password
```

Do not commit the `.env` file to GitHub. Add it to `.gitignore` so that passwords, database credentials, and secret keys remain private.

---

### 1.4 Database Provisioning

Mara Guard uses **PostgreSQL** to store system information.

The production database is provisioned using **Heroku Postgres**.

The backend uses:

* **SQLAlchemy** to work with the database.
* **Alembic** to manage database changes and migrations.

Apply existing database migrations using:

```bash
alembic upgrade head
```

When database models are changed, create a new migration using:

```bash
alembic revision --autogenerate -m "Describe the database change"
```

The database structure and relationships can be viewed in the [Mara Guard ERD and Database Documentation](https://docs.google.com/document/d/1T9SFUMPiJgdMtd4V8dAsmghw_5T8kx3IO69JV-2Q564/edit?tab=t.0#heading=h.zcyndk9u5wmy).

---

### 1.5 Deployment Workflow

The backend is deployed to **Heroku** using the production-ready code from the `main` branch.

The project contains a `Procfile` that tells Heroku how to start the FastAPI application:

```text
web: uvicorn main:app --host 0.0.0.0 --port \$PORT
```

For a manual deployment, use:

```bash
git push heroku main
```

Before deploying, make sure that:

1. The required changes have been committed.
2. The relevant tests have passed.
3. Database migrations are up to date.
4. Required environment variables are configured.
5. The application is ready for production.

---

### 1.6 Secure Environment Management

Sensitive information must not be stored directly in the source code.

This includes:

* Database credentials
* JWT secret keys
* MQTT usernames
* MQTT passwords
* Other private configuration values

For local development, these values are stored in the `.env` file.

For production, sensitive values are stored in **Heroku Config Vars**.

Never commit `.env` files or production secrets to GitHub.

---

### 1.7 Post-Deployment Verification

After deploying the backend, check that:

* The API is accessible.
* The [Mara Guard API Documentation](https://maraguard-3686f239afe8.herokuapp.com/docs) opens correctly.
* Ranger authentication works.
* Protected endpoints require authentication.
* Lion detection information can be retrieved.
* Battery and device information can be retrieved.
* Database operations are working correctly.
* No critical errors are reported.


## 2. Dashboard Deployment

### 2.1 Why the Dashboard is deployed

The **Mara Guard Dashboard** is the main web interface used by **rangers** to monitor lion activity and the status of field devices.

It provides information such as:

* **Lion detection counts** from field nodes
* **Battery levels** of solar-powered devices
* **System health and device status**
* **Historical detection information**
* **Alerts and monitoring information**

The Dashboard is built with **Next.js, React, TypeScript, Tailwind CSS, MQTT, and Recharts**.

**Repository:**
[View Dashboard Repository](https://github.com/akirachix/Voxels_Dashboard)

**Live Dashboard:**
[View Deployed Dashboard](https://voxels-p5s54890v-esther9.vercel.app/)

---

### Prerequisites

Before working on the Dashboard, make sure you have:

* Node.js installed
* npm installed
* Git installed
* Access to the required environment variables

The project uses:

| Technology   | Version |
| ------------ | ------- |
| Next.js      | 16.3.0  |
| React        | 19.2.8  |
| TypeScript   | 5.x     |
| Tailwind CSS | 4.x     |
| MQTT         | 5.15.2  |
| Recharts     | 3.10.1  |

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/akirachix/Voxels_Dashboard.git
cd Voxels_Dashboard
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the project root and add the required environment variables.

Do not commit the `.env` file to Git.

Sensitive information such as API endpoints, MQTT credentials, and secret keys should be stored in environment variables rather than directly in the source code.

### 4. Run the Dashboard Locally

Start the development server:

```bash
npm run dev
```

The application will normally be available at:

```text
http://localhost:3000
```

---

## Main Dashboard Functions

### Lion Detection Monitoring

The Dashboard displays information about lions detected by the field nodes.

Rangers can monitor:

* Number of lions detected
* Detection events
* Detection history
* Related alert information

### Battery Monitoring

The Dashboard displays the battery status of the solar-powered field devices.

This helps rangers monitor device power levels and identify equipment that may require attention.

### System Monitoring

The Dashboard provides visibility into the status of connected Mara Guard devices and system information received from the field.

### Historical Information

Rangers can review previously recorded detection information and system data to understand lion activity over time.

---

## Data Communication

The Dashboard communicates with the Mara Guard backend and IoT infrastructure to receive system information.

**MQTT** is used for relevant real-time telemetry, while **API requests** are used to access backend services and stored information.

The Dashboard can receive and display information such as:

* Lion detection counts
* Battery levels
* Detection events
* System status
* Historical detection information
* Alerts

---

## State Management

The Dashboard uses React functionality such as:

* `useState`
* `useEffect`
* React Hooks

These are used to manage information displayed in the interface, including detection counts, battery levels, alerts, and system status.

---

## Routing

The Dashboard uses **Next.js routing** to organise the different pages and views of the application.

Pages are organised according to their purpose to provide a clear experience for rangers monitoring the Mara Guard system.

---

## Styling and Interface

The Dashboard uses **Tailwind CSS** for responsive styling.

The interface is designed to work across different screen sizes so that rangers can access important monitoring information from desktop, tablet, or mobile devices.

Charts and visual data representations are supported using **Recharts**.

Icons and interface elements are supported using **Lucide React**.

[View Figma Design Board](https://www.figma.com/files/team/1649470842069931835/recents-and-sharing/recently-viewed?fuid=1643172383907410291)

---

## Security

The Dashboard follows basic security practices to protect system information and credentials.

### Environment Variables

Sensitive configuration values must be stored in `.env` files and must not be committed to the repository.

### Git Protection

The `.env` file should be included in `.gitignore` to prevent credentials from being pushed to GitHub.

### Secure Communication

Communication with deployed services should use secure protocols such as **HTTPS** and secure MQTT connections where applicable.

---

## Testing and Code Quality

Before creating a Pull Request, developers should check that the Dashboard builds and passes linting.

Run:

```bash
npm run lint
```

To create a production build:

```bash
npm run build
```

To run the production build locally:

```bash
npm start
```

The project also uses **Playwright** for end-to-end testing where applicable.

---

## Deployment

The Mara Guard Dashboard is deployed using **Vercel**.

The deployment is connected to the Dashboard repository:

[View Dashboard Repository](https://github.com/akirachix/Voxels_Dashboard)

### Deployment Process

1. Create a feature branch.
2. Make and test the required changes.
3. Run linting and relevant tests.
4. Create a Pull Request.
5. Review and merge the approved changes.
6. Vercel builds and deploys the updated application.
7. Verify that the deployed Dashboard is working correctly.

### Live Deployment

[View Deployed Dashboard](https://voxels-p5s54890v-esther9.vercel.app/)

---

## Package Information

The Dashboard uses the following main dependencies:

```json
{
  "name": "mara-guard",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint"
  },
  "dependencies": {
    "@tanstack/react-form": "^1.33.5",
    "lucide-react": "^1.34.0",
    "mqtt": "^5.15.2",
    "next": "16.3.0",
    "react": "19.2.8",
    "react-dom": "19.2.8",
    "recharts": "^3.10.1"
  },
  "devDependencies": {
    "@tailwindcss/postcss": "^4",
    "@types/node": "^20",
    "@types/react": "^19",
    "@types/react-dom": "^19",
    "eslint": "^9",
    "eslint-config-next": "16.3.0",
    "tailwindcss": "^4",
    "typescript": "^5"
  }
}
```

# 4. Mobile Application Deployment

## 4.1 Overview

The **Mara Guard Mobile Application** is a mobile component of the Mara Guard system. It supports users by providing access to system information and monitoring features related to lion activity, device status, and battery levels.

**Repository:**

[View Mobile Repository](https://github.com/akirachix/Voxels_Mobile)

### The Mission

Human-wildlife conflict threatens both pastoralist livelihoods and endangered predator populations. Mara Guard secures the critical buffer zones to stop lions from moving out of wildlife areas and wandering into Maasai residential zones. By replacing passive fencing with an active, automated defense grid, we provide immediate protection that keeps both grazing livestock and local communities safe.

---

## 4.2 App Architecture & Features

This codebase uses a **Screen-First Layered Architecture** to support smooth group development. Files are isolated so team members can build standalone interface modules and views simultaneously without experiencing version conflicts.

### 4.2.1 Active App Module

The application is organised into the following main architectural areas:

* **Global Architecture Core (`lib/models/core`)**
  Provides universal state blueprints, data serialization layers, and underlying repository rules.

* **Security Portal (`lib/Screens/Auth`)**
  Provides secure user onboarding, sign-in, and account registration flows.

* **Shared Layout Constants (`lib/constants`)**
  Contains static variables, styling dimensions, network path endpoints, and system layout assets.

* **Application Design System (`lib/theme`)**
  Manages colour palettes, text scales, and geometric decorations for consistent views.

* **Universal Interface Blocks (`lib/widgets`)**
  Contains reusable structural fragments and UI elements shared across multiple screens.

* **Interface Presentation Viewports (`lib/screens`)**
  Contains the complete surface layer holding localized page structures, layout logic, and modular user features.

The main project structure is:

```text
lib/
├── models/core/              # Global data models and core architectural files
├── constants/                # Universal design constants, spacing configurations, and assets
├── theme/                    # App-wide colour styling and typography
├── widgets/                  # Reusable UI components and global elements
├── screens/                  # Interface pages and presentation layout boundaries
│   ├── Auth/                 # User identity, onboarding, and secure login modules
│   ├── battery-levels/       # Hardware monitor displaying active node battery metrics
│   ├── HomeScreen/           # Core operational hub displaying radar feeds and threat scales
│   ├── lion-counts/          # Analytical data presenting seasonal tracking counts
│   ├── log-out/              # Secure application session clearing and gateway exits
│   └── settings/             # Device calibration and manual override controls
└── main.dart                 # Application entry point and initialization
```

---

### 4.2.2 Welcome & Onboarding

The authentication area is located under `lib/Screens/Auth`.

It provides:

* **Get Started View:** Introduction to the Mara Guard community portal.
* **Account Creation:** Secure forms for local livestock owners and community scouts.
* **Sign-in:** User authentication and secure access.

---

### 4.2.3 Main Status Dashboard

The main dashboard is located under `lib/Screens/HomeScreen`.

It provides:

* **Live System Monitor:** Visual dashboard showing whether hardware nodes are online.
* **Threat Level Gauge:** Quick indicator showing current area risk based on recent detections.
* **Recent Activity Feed:** Scrollable log of recent movements flagged by the radar.

---

### 4.2.4 Solar & Battery Health Tracker

The battery monitoring section provides information about the status of the solar-powered field devices.

It allows users to monitor active node battery metrics and identify devices that may require attention.

---

### 4.2.5 Lion Counts

The `lion-counts` section provides analytical information about lion detection and tracking.

This supports monitoring of detection counts and activity over time.

---

### 4.2.6 Settings

The `settings` section provides access to device-related configuration and manual control features.

---

### 4.2.7 Log Out

The `log-out` section provides a secure way for users to clear their application session and exit the application.

---

## 4.3 Prerequisites and System Configuration

Before running the application, ensure your environment meets the following requirements:

* **Flutter SDK:** Install the latest stable version of Flutter from the [official Flutter website](https://flutter.dev/).
* **Dart SDK:** Automatically bundled with the Flutter SDK.
* **Java Development Kit (JDK):** Required for Android builds. JDK 17 is recommended.
* **Android Studio / Xcode:** Required for mobile platform compilation and simulators.
* **Environment Variables:** Ensure `flutter` is added to your system's PATH.

---

## 4.4 Getting Started

### 4.4.1 Clone the Repository

The Mobile Application source code is available in the following repository:

[View Mobile Repository](https://github.com/akirachix/Voxels_Mobile)

Clone the repository:

```bash
git clone https://github.com/akirachix/Voxels_Mobile.git
cd Voxels_Mobile
```

### 4.4.2 Verify the Flutter Environment

Run:

```bash
flutter doctor
```

This checks whether the required Flutter development tools are correctly installed.

### 4.4.3 Install Dependencies

Fetch the packages declared in `pubspec.yaml`:

```bash
flutter pub get
```

If necessary, clean previous build artifacts using:

```bash
flutter clean
```

### 4.4.4 Check Connected Devices

List available physical devices and emulators:

```bash
flutter devices
```

### 4.4.5 Run the Application

Run the application in Debug mode:

```bash
flutter run
```

For Release mode:

```bash
flutter run --release
```

---

## 4.5 Dependencies (`pubspec.yaml`)

The Mobile Application uses the following packages to support state management, network communication, charts, local storage, and icons:

```yaml
dependencies:
  flutter:
    sdk: flutter

  # State Management and Dependency Injection
  provider: ^6.1.2

  # Network HTTP Client for backend integration
  http: ^1.2.1

  # Data Visualization for Lion Tracking and Battery Metrics
  fl_chart: ^0.66.0

  # Local Storage for secure user sessions
  flutter_secure_storage: ^9.0.0

  # Decorative UI elements and vector assets
  cupertino_icons: ^1.0.6
```

---

## 4.6 Data Communication

The Mobile Application communicates with the Mara Guard backend to access relevant system information.

Network communication is supported through the `http` package.

The application can access information related to:

* Lion detection
* Lion counts
* Battery levels
* System status
* Detection activity
* User information
* Other Mara Guard system information

---

## 4.7 State Management

The application uses **Provider** for state management and dependency injection.

State management allows the application to handle and update information displayed across different screens.

This includes information such as:

* Lion detection information
* Battery levels
* System status
* User session information
* Application data

---

## 4.8 Local Storage

The Mobile Application uses **flutter_secure_storage** for secure local storage.

This supports the storage of sensitive user session information without placing credentials directly in the application source code.

---

## 4.9 User Interface and Data Visualisation

The Mobile Application provides mobile-friendly interfaces for monitoring Mara Guard information.

**FL Chart** is used to support data visualisation for information such as:

* Lion tracking
* Lion detection counts
* Battery metrics

The application also uses reusable widgets and a central theme to maintain consistency across its screens.

---

## 4.10 Security

The Mobile Application follows basic security practices to protect user and system information.

### 4.10.1 Secure Local Storage

Sensitive user session information is handled using `flutter_secure_storage`.

### 4.10.2 Environment Configuration

Ensure production tokens, server links, and local API keys are stripped before generating distribution packages or committing changes back into open repositories.

Sensitive configuration values should not be stored directly in the application source code.

Where environment variables or configuration values contain sensitive information, they should be kept private and excluded from version control.

---

### 4.10.3 Secure Communication

Communication with deployed backend services should use secure protocols such as **HTTPS** where applicable.

---

## 4.11 Testing and Code Quality

Before creating a Pull Request, developers should verify that the Mobile Application builds and runs correctly.

Developers should check that:

* The application starts successfully.
* Navigation works correctly.
* Authentication works correctly.
* Backend communication works correctly.
* Detection information displays correctly.
* Battery information displays correctly.
* Charts and visualisations load correctly.
* No critical errors are reported.

---

## 4.12 Compilation and Build Packages

### 4.12.1 Android App Bundle

Generate a release Android App Bundle for Google Play:

```bash
flutter build appbundle
```

---

### 4.12.2 Android APK

Generate a release Android APK:

```bash
flutter build apk
```

---

### 4.12.3 iOS Build

Generate a release iOS application bundle.

This requires macOS and Xcode:

```bash
flutter build ios
```
