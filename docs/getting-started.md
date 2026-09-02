# Getting Started

This guide explains how to set up the Mara Guard development environment. Mara Guard is divided into separate repositories for the website, dashboard, backend, IoT system, and mobile application.

## Prerequisites

Install the tools required for the component you will be working on:


**Git** Source code management        
**Node.js & npm** Website and dashboard         
**Python** Backend and related services  
**Flutter & Dart** Mobile application            
**Postman** API testing                   
**Cypress** End-to-end testing            
**Playwright** Automated application testing 
**Arduino IDE / PlatformIO** IoT development               


## Repositories

Clone the repository for the component you are working on:

### Voxels Informational Website

**(https://github.com/akirachix/Voxels_Informational_Website)**

### Voxels Dashboard / PWA

**(https://github.com/akirachix/Voxels_Dashboard)**

### Voxels Backend / API

**(https://github.com/akirachix/Voxels_Backend)**

### Voxels IoT

**(https://github.com/akirachix/Voxels_IoT)**

### Voxels Mobile

**(https://github.com/akirachix/Voxels_Mobile)**               

## Environment Setup

Before running a project:

1. Open the relevant repository.
2. Check its README and configuration files.
3. Create the required environment variables.
4. Install the project dependencies.
5. Start the application or service using its documented command.

**Do not commit API keys, passwords, tokens, or other secrets to Git.**

## Installing Dependencies

Use the package manager required by each repository.

### Node.js Projects

For the website and dashboard:
<div style="background-color: #2b1d16; padding: 20px; border-radius: 8px; border: 1px solid #453227; color: #e1dbd6 !important; font-family: 'Fira Mono', monospace; margin: 15px 0;">
<code>npm install</code>
</div>

### Mobile Application

For the Flutter application:

<div style="background-color: #2b1d16; padding: 20px; border-radius: 8px; border: 1px solid #453227; color: #e1dbd6 !important; font-family: 'Fira Mono', monospace; margin: 15px 0;">
<code>flutter pub get</code>
</div>

### Backend and IoT

Install the dependencies using the instructions provided in the respective repository.

## Running the Project

Each component has its own development process. Refer to the README in the relevant repository for the exact command required to start the application or service.

Before running a component, ensure that its required dependencies, environment variables, and supporting services are configured.

## Testing

Mara Guard uses the following testing tools:

* **Postman** — API testing
* **Cypress** — end-to-end testing
* **Playwright** — automated application testing

Use the testing commands provided in the relevant repository.

## Verify Your Setup

Your development environment is ready when:

* Dependencies install successfully.
* Required environment variables are configured.
* The application or service starts without errors.
* Required services can be reached.
* Relevant tests run successfully.

For component-specific instructions, refer to the documentation for the **Website, Dashboard, Backend, IoT, or Mobile** component.
