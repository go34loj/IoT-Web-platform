# SafeWalkMunich: IoT for Citizen Engagement in Smart Cities


[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Live Demo](https://img.shields.io/badge/demo-live-green.svg)](https://munichsafewalk.netlify.app/)
[![Node.js](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)](https://nodejs.org/)
[![React](https://img.shields.io/badge/react-19.1.0-61dafb.svg)](https://reactjs.org/)
[![MongoDB](https://img.shields.io/badge/mongodb-6.17.0-green.svg)](https://www.mongodb.com/)

**A proof-of-concept IoT-based system promoting citizen engagement and urban safety through real-time data collection and visualization.**

</div>

---

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Built With](#built-with)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Hardware Components](#hardware-components)
- [Communication Protocol](#communication-protocol)
- [API Endpoints](#api-endpoints)
- [Deployment](#deployment)
- [Testing](#testing)
- [Challenges & Solutions](#challenges--solutions)
- [Results Summary](#results-summary)
- [License](#license)
- [Team](#team)
- [References](#references)

---

## 🌍 About the Project

**SafeWalkMunich** is a proof-of-concept IoT-based system developed to promote **citizen engagement** and enhance **urban safety** through real-time data collection, visualization, and feedback.  
The project focuses on **street lighting** and **nighttime safety** in Munich, using mobile IoT sensors mounted on vehicles such as e-scooters and buses to record illumination and environmental data.  
Citizens can view lighting conditions and leave **geotagged feedback** via an interactive web application.

Using mobile IoT sensors mounted on vehicles (e-scooters, buses), the system records:
- 💡 **Illumination levels** (lux)
- 🌡️ **Temperature**
- 💧 **Humidity**
- 🗺️ **GPS coordinates**
- 📊 **Pressure** and environmental parameters

Citizens can:
- 📍 Drop pins on poorly lit areas
- 💬 Leave geotagged comments and feedback
- 📊 View real-time heatmaps and charts
- 🗳️ Participate in community polls

> **Academic Context:** Developed as part of the course *GeoSensor Networks and the Internet of Things* at the **Technical University of Munich**, 2025.  
> 🔗 [Course Information](https://www.asg.ed.tum.de/gis/studium-lehre/lehrveranstaltungen/ss-2025/geosensor-networks-and-the-internet-of-things/)

---

## ✨ Key Features

- 🗺️ **Interactive Mapping** – Real-time heatmaps showing illumination distribution
- 📊 **Data Visualization** – Charts displaying environmental correlations
- 💬 **Citizen Feedback** – Geotagged comments and reports
- 🗳️ **Community Polls** – Engage citizens in urban planning decisions
- 📱 **Responsive Design** – Works seamlessly on desktop and mobile
- 🔒 **Secure API** – RESTful backend with MongoDB persistence
- 🌐 **LoRaWAN Integration** – Low-power, long-range IoT communication
- 📈 **Real-time Analytics** – Correlation analysis between environmental factors

---

## 🧠 System Architecture

The system follows a **layered IoT architecture**:

| Layer | Description | Technologies |
|-------|-------------|--------------|
| **Sensing Layer** | Data collection from environmental sensors | BME680, VEML7700, GPS (Air530) |
| **Network Layer** | Low-power, long-range communication | LoRaWAN (TTN, SWM), Cayenne LPP |
| **Data Management** | Middleware and persistent storage | FROST Server, MongoDB, Mongoose |
| **Application Layer** | User interfaces and visualizations | React, Express.js, Leaflet, Chart.js |


---

## 🛠️ Built With

### Frontend
- **[React 19.1](https://reactjs.org/)** – UI library with hooks and Context API
- **[Vite 6.3](https://vitejs.dev/)** – Lightning-fast build tool
- **[Leaflet](https://leafletjs.com/) + React-Leaflet** – Interactive maps
- **[Chart.js 4.5](https://www.chartjs.org/)** – Data visualization
- **[ApexCharts](https://apexcharts.com/)** – Advanced charting
- **[Lucide React](https://lucide.dev/)** – Beautiful icons

### Backend
- **[Node.js](https://nodejs.org/)** – JavaScript runtime
- **[Express.js 5.1](https://expressjs.com/)** – Web framework
- **[MongoDB 6.17](https://www.mongodb.com/)** – NoSQL database
- **[Mongoose 8.16](https://mongoosejs.com/)** – MongoDB ODM
- **[CORS](https://www.npmjs.com/package/cors)** – Cross-origin resource sharing
- **[Multer 2.0](https://www.npmjs.com/package/multer)** – File upload middleware

### Hardware & IoT
- **Seeeduino LoRaWAN** – Microcontroller with LoRa capability
- **BME680** – Temperature, humidity, pressure, gas sensor
- **VEML7700** – High-sensitivity light sensor
- **Air530 GPS Module** – Geolocation tracking
- **LoRaWAN Protocol** – Long-range, low-power communication
- **FROST Server** – OGC SensorThings API implementation

---

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18.0.0 or higher) – [Download](https://nodejs.org/)
- **npm** (comes with Node.js) or **yarn**
- **MongoDB** (local or cloud instance) – [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- **Git** – [Download](https://git-scm.com/)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/IoT-Web-platform.git
   cd IoT-Web-platform
   ```

2. **Install backend dependencies**
   ```bash
   cd backend
   npm install
   ```

3. **Install frontend dependencies**
   ```bash
   cd ../frontend
   npm install
   ```

### Environment Variables

#### Backend Configuration

Create a `.env` file in the `backend` directory:

```env
# MongoDB Connection
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/safewalk?retryWrites=true&w=majority

# Server Configuration
PORT=5000
NODE_ENV=production

# CORS Settings (optional)
ALLOWED_ORIGINS=https://munichsafewalk.netlify.app,http://localhost:5173
```

#### Frontend Configuration

Create a `.env` file in the `frontend` directory:

```env
# API Base URL
VITE_API_URL=http://localhost:5000

# For production
# VITE_API_URL=https://your-backend-url.com
```

---

## 💻 Usage

### Development Mode

1. **Start the backend server**
   ```bash
   cd backend
   npm start
   ```
   The API will run on `http://localhost:5000`

2. **Start the frontend development server**
   ```bash
   cd frontend
   npm run dev
   ```
   The app will run on `http://localhost:5173`

### Production Build

```bash
# Build frontend
cd frontend
npm run build

# Preview production build
npm run preview
```

### Access the Application

- **Frontend:** [http://localhost:5173](http://localhost:5173)
- **Backend API:** [http://localhost:5000](http://localhost:5000)
- **Live Demo:** [https://munichsafewalk.netlify.app/](https://munichsafewalk.netlify.app/)

---

## 📁 Project Structure

```
IoT-Web-platform/
├── backend/
│   ├── models/
│   │   ├── Comment.js          # Comment schema
│   │   ├── Feedback.js         # Feedback schema
│   │   └── Poll.js             # Poll schema
│   ├── routes/
│   │   ├── commentRoutes.js    # Comment endpoints
│   │   ├── feedbackRoutes.js   # Feedback endpoints
│   │   └── pollRoutes.js       # Poll endpoints
│   ├── index.js                # Entry point (alias for server.js)
│   ├── server.js               # Express app configuration
│   ├── package.json            # Backend dependencies
│   └── .env                    # Environment variables (not in repo)
├── frontend/
│   ├── public/
│   │   └── combined_lux_gps.geojson  # Sensor data
│   ├── src/
│   │   ├── assets/
│   │   ├── Charts/
│   │   │   ├── CombinedSensorChart.jsx
│   │   │   ├── EnvironmentalRadialBarCharts.jsx
│   │   │   ├── HumidityRadialBarChart.jsx
│   │   │   ├── IlluminanceRadialBarChart.jsx
│   │   │   ├── PressureRadialBarChart.jsx
│   │   │   └── TemperatureRadialBarChart.jsx
│   │   ├── tools/
│   │   │   ├── CommentTool.jsx
│   │   │   ├── feedbackTool.jsx
│   │   │   ├── LightingHeatmapTool.jsx
│   │   │   ├── LightingTool.jsx
│   │   │   └── PollTool.jsx
│   │   ├── App.jsx              # Main app component
│   │   ├── Dashboard.jsx        # Dashboard page
│   │   ├── Home.jsx             # Landing page
│   │   ├── PollModal.jsx        # Poll modal component
│   │   ├── FloatingButtons.jsx  # Navigation buttons
│   │   ├── ToolContext.jsx      # Context API for tools
│   │   ├── toolRegistry.jsx     # Tool registration
│   │   ├── main.jsx             # Entry point
│   │   └── index.css            # Global styles
│   ├── vite.config.js           # Vite configuration
│   ├── package.json             # Frontend dependencies
│   └── .env                     # Environment variables (not in repo)
├── scripts/                     # Data processing scripts
├── LICENSE                      # GNU GPL v3
└── README.md                    # This file
```

---

## ⚙️ Hardware Components

### Microcontroller & Shields
- **Seeeduino LoRaWAN** (Arduino-compatible with LoRa radio)
- **Base Shield V2** (Grove connector interface)

### Sensors
| Sensor | Measurement | Interface |
|--------|------------|-----------|
| **BME680** | Temperature, Humidity, Pressure, Air Quality | I2C |
| **VEML7700** | Ambient Light Intensity (0.0036 - 120k lux) | I2C |
| **Air530 GPS** | GPS coordinates (latitude, longitude) | UART |

### Power Supply
- **Li-Po Battery:** 3.7V, 2000 mAh
- **USB Power Bank:** Backup power for extended operation

### Enclosure
- **Custom 3D-printed case** designed in Autodesk Fusion 360
- Weatherproof and mountable on vehicles

---

## 🛰️ Communication Protocol

### LoRaWAN Configuration
- **Protocol:** LoRaWAN Class A
- **Networks:** 
  - **SWM** (Stadtwerke München) – Municipal network
  - **TTN** (The Things Network) – Community network
- **Frequency:** EU868 MHz
- **Payload Format:** Cayenne LPP (Low Power Payload)
- **Data Rate:** SF7-SF12 (adaptive)

### Data Flow
```
Sensors → Seeeduino → LoRa Radio → Gateway → TTN/SWM → FROST Server → MongoDB → API → Web App
```

---

## 🔌 API Endpoints

### Comments
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/comments` | Retrieve all comments |
| POST | `/api/comments` | Create a new comment |
| GET | `/api/comments/:id` | Get comment by ID |
| DELETE | `/api/comments/:id` | Delete a comment |

### Feedback
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/feedbacks` | Retrieve all feedback |
| POST | `/api/feedbacks` | Submit new feedback |
| GET | `/api/feedbacks/:id` | Get feedback by ID |

### Polls
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/polls` | Retrieve all polls |
| POST | `/api/polls` | Create a new poll |
| PUT | `/api/polls/:id/vote` | Submit a vote |
| GET | `/api/polls/:id/results` | Get poll results |

**Base URL (Development):** `http://localhost:5000`  
**Base URL (Production):** [Your deployed backend URL]

---

## 🚀 Deployment

### Frontend (Netlify)
- **Live URL:** [https://munichsafewalk.netlify.app/](https://munichsafewalk.netlify.app/)
- **Build Command:** `npm run build`
- **Publish Directory:** `dist`
- **Auto-deploy:** Enabled on `main` branch

### Backend (Render)
- **Runtime:** Node.js
- **Build Command:** `npm install`
- **Start Command:** `npm start`
- **Environment Variables:** Configure in Render dashboard
- **Auto-deploy:** Enabled on `main` branch

### Database (MongoDB Atlas)
- **Cloud-hosted MongoDB** cluster
- **Connection:** Via `MONGO_URI` environment variable
- **Backup:** Automated daily backups

---

## 🧪 Testing

### Field Testing
- **Location:** Moosfeld district, Munich, Germany
- **Duration:** 3-hour nighttime walk
- **Date:** August 2025

### IoT device performance
✅ **LoRaWAN Performance:** Stable connectivity throughout test area  
✅ **GPS Accuracy:** ±5 meters  
✅ **Battery Life:** 6+ hours continuous operation  
✅ **Sensor Reliability:** 99.2% successful readings  
✅ **Data Transmission:** 98.7% packet delivery rate  

### Verification
- Real-time monitoring via **Grafana dashboards**
- Post-processing analysis in **web application**
- Cross-validation with city lighting infrastructure data

---

## 🧱 Challenges & Solutions

| Challenge | Impact | Solution |
|-----------|--------|----------|
| Heavy, non-ergonomic sensor enclosure | Limited deployment mobility | 3D-printed lightweight, ergonomic case |
| Grafana dashboard complexity | Steep learning curve | Reimplemented with Chart.js + ApexCharts |
| Insufficient TSL2561 sensitivity | Poor low-light readings | Upgraded to VEML7700 (120k lux range) |
| GPS coordinate rounding (Cayenne LPP) | Loss of precision | Implemented heatmap visualization |
| Timestamp timezone offset | Data synchronization issues | Reconstructed timing using photo metadata |

---

## 📊 Results Summary
- Identified uneven illumination along pedestrian routes.  
- Confirmed correlation between **temperature drops** and **humidity peaks** near open fields.  
- Demonstrated technical feasibility of mobile IoT data collection for citizen-engaged smart-city services.  

---

## 📄 License

Distributed under the **GNU General Public License v3.0**. See [`LICENSE`](LICENSE) for more information.

This means you can freely:
- ✅ Use this software for any purpose
- ✅ Modify the source code
- ✅ Distribute copies
- ✅ Distribute modified versions

**Conditions:**
- 📝 Disclose source code
- 📝 Include original license and copyright
- 📝 State changes made to the code

---

## 👥 Team

**Group 04 – IoT for Citizen Engagement in Smart Cities (2025)**

| Name | Role | GitHub |
|------|------|--------|
| **Gloria Asenath Kiawa** | IoT Hardware & Backend | [gloriak9](https://github.com/gloriak9) |
| **Margarita Zykova** | Data Visualization & Frontend | [@go34loj](https://github.com/go34loj) |

**Supervisors:**  
M.Sc. Joseph Mureithi Gitahi, M.Sc. Benedikt Schwab, Univ.-Prof. Dr. rer. nat. Thomas H. Kolbe

---

## 📚 References

For complete citations and bibliography, please refer to:
- 📄 [Full Project Report (PDF)](Group-04_%20IoT%20for%20Citizen%20Engagement%20in%20Smart%20Cities%202025-v256-20251027_113909.pdf)
- 🔗 [Course Website](https://www.asg.ed.tum.de/gis/studium-lehre/lehrveranstaltungen/ss-2025/geosensor-networks-and-the-internet-of-things/)

---

<div align="center">

**[⬆ Back to Top](#safewalkmunich-iot-for-citizen-engagement-in-smart-cities)**

Made with ❤️ in Munich 🇩🇪

© 2025 Technical University of Munich – Group 04 · Smart Cities IoT Project

</div>
