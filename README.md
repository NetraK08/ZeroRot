# ZeroRot

### Solar-Powered Smart Mini Cold Storage System for Fresh Vegetables

ZeroRot is a solar-powered, smart mini cold storage system designed to reduce post-harvest losses of fresh vegetables and horticultural produce in regions where reliable cold-chain infrastructure and electricity are limited.

The system combines an energy-efficient cooling chamber, solar power, battery backup, IoT-based monitoring, and a web dashboard to provide farmers, cooperatives, collection centres, and local markets with an affordable decentralized cold-storage solution.

---

## Problem Statement

Fresh vegetables such as tomatoes, cabbage, beans, leafy vegetables, chilli, and other horticultural crops are highly perishable. In areas with limited cold-storage infrastructure, unreliable electricity, difficult terrain, and transportation delays, farmers are often forced to sell their produce immediately or risk significant post-harvest losses.

ZeroRot addresses this problem by providing a compact and modular cold-storage system that can operate using solar energy and monitor storage conditions in real time.

---

## Objectives

* Reduce post-harvest losses of fresh vegetables.
* Provide affordable decentralized cold storage for rural communities.
* Operate primarily using renewable solar energy.
* Maintain suitable temperature and humidity conditions.
* Monitor storage conditions in real time.
* Provide alerts for unsafe temperature, low battery, and power failure.
* Enable operation during temporary internet or grid-power outages.
* Provide a simple web-based interface for monitoring and management.
* Develop a scalable solution suitable for farmer groups, cooperatives, collection centres, and local markets.

---

## Key Features

### Smart Environmental Monitoring

* Live temperature monitoring
* Live humidity monitoring
* Temperature history and graphs
* Storage condition status
* Door status monitoring

### Energy Management

* Solar power monitoring
* Battery percentage monitoring
* Compressor status monitoring
* Power availability monitoring
* Battery backup during power interruptions

### Alerts

* High-temperature alerts
* Low-battery alerts
* Power-failure alerts
* Connectivity/offline status
* System fault monitoring

### Model Render
<img width="1291" height="1055" alt="088700f0-8740-4c9c-9c5a-801203abd3a1" src="https://github.com/user-attachments/assets/1a790d0c-a8a3-4548-8ec3-dbf6dbbe30a9" />
<img width="1600" height="900" alt="18f00e16-6e27-44ba-9cb8-a4ae3d66aeff" src="https://github.com/user-attachments/assets/b9999a42-02c9-41d0-b44f-0c61d2472f7b" />
<img width="1600" height="900" alt="78a93a24-3db2-4a6d-a3df-0d0f32cb071b" src="https://github.com/user-attachments/assets/9e52db77-014c-4ac2-988e-79e7ab3b704d" />

### Offline Operation

The system is designed with an offline-first approach. Sensor data can be temporarily stored locally when internet connectivity is unavailable and synchronized with the backend when connectivity is restored.

### Web Dashboard

The ZeroRot dashboard provides a centralized interface for monitoring:

* Temperature
* Humidity
* Battery level
* Solar power
* Compressor status
* Temperature trends
* Alerts
* Storage status
* System connectivity

<img width="2879" height="1557" alt="image" src="https://github.com/user-attachments/assets/bcbbec3a-eccf-404b-8db3-f6744e293183" />

---

## System Architecture

```text
Temperature / Humidity Sensors
             |
             v
           ESP32
             |
      +------+------+--------------------> On Device Display
      |             |
      v             v
Cooling Control   Data Processing
      |             |
      v             v
   Peltier       Wi-Fi / IoT
    Module          |
                    v
             Supabase Backend
                    |
          +---------+---------+
          |                   |
          v                   v
      PostgreSQL         Authentication
          |
          v
   ZeroRot Web Dashboard
          |
          v
   Monitoring & Alerts
```

---

## Technologies Used

### Frontend

* HTML5
* CSS3
* JavaScript
* JavaScript charting libraries where required
* Responsive web design

### Backend

* Supabase
* PostgreSQL
* Supabase Authentication
* Supabase APIs

### Hardware

* ESP32 microcontroller
* Temperature sensor
* Humidity sensor
* Battery monitoring system
* Solar power monitoring
* Compressor-based cooling system
* Solar panels
* Battery backup
* Insulated storage chamber

### Connectivity

* Wi-Fi for the initial prototype
* Local data storage for offline operation
* 4G/GSM connectivity planned for deployment-stage versions

---

## Methodology

### 1. Data Collection

Sensors continuously collect temperature, humidity, battery, solar power, and system status data from the cold-storage unit.

### 2. Local Processing

The ESP32 processes sensor readings and performs basic system control. Temperature thresholds are used to determine compressor operation.

### 3. Cooling Control

The cooling system operates using predefined temperature limits and hysteresis to prevent unnecessary compressor switching.

Example:

```text
Temperature > Upper Limit
        |
        v
 Compressor ON
        |
        v
Temperature reaches Lower Limit
        |
        v
 Compressor OFF
```

The exact operating temperature range can be adjusted according to the vegetables being stored.

### 4. Data Transmission

The ESP32 sends sensor readings to the backend through Wi-Fi.

### 5. Backend Storage

Supabase PostgreSQL stores sensor readings, system information, alerts, and historical data.

### 6. Dashboard Visualization

The web dashboard retrieves the stored data and displays real-time readings, historical graphs, system status, and alerts.

### 7. Offline Storage

If internet connectivity is lost:

```text
Internet Available
       |
       v
Send Data to Supabase
       |
       v
Display on Dashboard

Internet Unavailable
       |
       v
Store Data Locally
       |
       v
Connection Restored
       |
       v
Synchronize with Supabase
```

---

## Dashboard

The ZeroRot web dashboard is designed around the core information required to operate and monitor the cold-storage unit.

### Overview

Displays:

* Current temperature
* Current humidity
* Battery percentage
* Solar power
* Compressor status
* Overall storage status

### Environment

Provides:

* Temperature monitoring
* Humidity monitoring
* Temperature history
* Environmental status

### Energy

Provides:

* Solar power generation
* Battery level
* Power availability
* Compressor status
* Energy usage information

### Alerts

Displays important system events such as:

* High temperature
* Low battery
* Power failure
* Sensor/connectivity issues

### Storage

Provides information about storage capacity and stored produce.

---

## Prototype Workflow

```text
             SOLAR PANEL
                  |
                  v
           Charge Controller
                  |
                  v
               BATTERY
                  |
          +-------+-------+
          |               |
          v               v
      Compressor       ESP32
          |               |
          v               v
     Cold Storage     Sensors
                          |
                          v
                       Wi-Fi
                          |
                          v
                      Supabase
                          |
                          v
                  ZeroRot Dashboard
```

---

## Current Prototype Scope

The initial prototype focuses on demonstrating the core functionality of ZeroRot:

1. Live temperature
2. Live humidity
3. Battery percentage
4. Solar power monitoring
5. Compressor status
6. Temperature history graph
7. High-temperature alert
8. Low-battery alert
9. Power-failure alert
10. Offline data storage and synchronization

The prototype may initially use simulated sensor data for dashboard development before integration with the physical ESP32 hardware.

---

## Future Scope

The following features are planned for later deployment stages:

* 4G/GSM connectivity
* SMS alerts
* Multi-unit cold-storage management
* Remote monitoring
* Advanced energy analytics
* Predictive spoilage analysis
* Produce-specific storage recommendations
* Automated humidity control
* Advanced IoT analytics
* Cloud-based reporting

Predictive spoilage analysis will require sufficient historical environmental and produce-condition data before being implemented reliably.

---

## Target Users

ZeroRot is intended primarily for:

* Farmers
* Farmer Producer Organizations (FPOs)
* Farmer cooperatives
* Village collection centres
* Local markets
* Agricultural aggregators
* Rural entrepreneurs

The system can support a community-based model where a cooperative or local organization owns the unit and farmers access storage through a rental or pay-per-use model.

---

## Expected Impact

ZeroRot aims to:

* Reduce vegetable wastage.
* Extend the usable storage period of fresh produce.
* Reduce pressure to sell produce immediately after harvest.
* Improve farmers' ability to access better market prices.
* Reduce dependence on unreliable grid electricity.
* Enable decentralized cold storage in remote areas.
* Promote renewable-energy-based agricultural infrastructure.

---

## Project Status

**Current Stage:** Prototype Development

The project is currently focused on developing the web dashboard, IoT monitoring architecture, and working hardware prototype.

### Development Roadmap

```text
Phase 1
System Design
    |
    v
Phase 2
Web Dashboard
    |
    v
Phase 3
Supabase Backend
    |
    v
Phase 4
ESP32 & Sensor Integration
    |
    v
Phase 5
Solar + Cooling Integration
    |
    v
Phase 6
Working Prototype
    |
    v
Phase 7
Testing & Optimization
    |
    v
Deployment
```

---

## Repository Structure

```text
ZeroRot/
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   ├── script.js
│   └── assets/
│
├── backend/
│   ├── database/
│   └── config/
│
├── hardware/
│   ├── esp32/
│   └── sensors/
│
├── docs/
│   ├── architecture/
│   └── diagrams/
│
└── README.md
```

---

## Installation and Setup

Clone the repository:

```bash
git clone https://github.com/<your-username>/ZeroRot.git
cd ZeroRot
```

Open the frontend:

```text
frontend/index.html
```

For backend integration, create a Supabase project and configure the required database tables, API credentials, and authentication settings.

The ESP32 firmware can then be configured with the required Wi-Fi and Supabase connection details.

> Never commit Supabase service-role keys, passwords, or other private credentials to the repository.

---

## Contribution

Contributions and improvements are welcome.

For major changes, please open an issue first to discuss the proposed modification. Pull requests should include a clear description of the changes and, where applicable, testing details.

---

## License

This project is currently intended as an academic and prototype development project.

A formal open-source license can be added when the project is ready for public distribution.

---

## Project Vision

**ZeroRot aims to make reliable cold storage more accessible to farmers by combining renewable energy, smart monitoring, and affordable decentralized infrastructure.**

The long-term goal is to create a scalable cold-storage network that can operate in areas where conventional cold-chain infrastructure is difficult or expensive to establish.
