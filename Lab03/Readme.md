# Lab 3

## Title: Visualizing IoT Sensor Data Using Interactive Dashboards

---

## Objectives

> 1. Retrieve stored sensor data from the REST API developed in Lab 2.
> 2. Understand the importance of data visualization in IoT systems.
> 3. Develop a web-based dashboard to display sensor data.
> 4. Create real-time and historical visualizations of temperature and humidity data.
> 5. Deploy the dashboard on the AWS EC2 instance.
> 6. Analyze sensor trends using graphical representations.

---

## Background Theory

### Data Visualization in IoT
IoT systems generate continuous sensor data such as temperature and humidity. Raw data is difficult to interpret directly, so visualization techniques are used to convert it into meaningful charts and graphs for better analysis and monitoring.

### API Oriented Architecture
In this architecture, frontend applications communicate with backend services using REST APIs. This ensures separation of frontend and backend, making the system scalable and maintainable.

### Dashboard Systems
A dashboard is a visual interface that displays real-time and historical data in graphical form. It helps in monitoring system performance and analyzing trends efficiently.

### Designing Data Filters
Data filters allow users to query specific ranges or time periods of sensor data. Filtering improves performance and helps focus on relevant data points for analysis.

---

## Procedure

### Step 1: Launch AWS EC2 Instance
- Login to AWS Management Console
- Launch Ubuntu EC2 instance




### Step 2: Update System

```bash
sudo apt update && sudo apt upgrade -y
```

### Step 3: Install Required Tools

```bash
sudo apt install python3-pip python3-venv -y
```

### Step 4: Create Project Directory

```bash
mkdir iot-dashboard
cd iot-dashboard
```

### Step 5: Create Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### Step 6: Install Dependencies

```bash
pip install fastapi uvicorn tinydb python-multipart
```

### Step 7: Project Structure

```
iot-dashboard/
│
├── main.py
├── db.json
├── venv/
└── static/
    └── index.html
```

### Step 8: Backend Code (FastAPI)

Create `main.py`:

```python
from fastapi import FastAPI
from tinydb import TinyDB
from datetime import datetime
from fastapi.staticfiles import StaticFiles
from fastapi.responses import FileResponse
from fastapi.middleware.cors import CORSMiddleware

app = FastAPI()

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_methods=["*"],
    allow_headers=["*"],
)

db = TinyDB("db.json")

app.mount("/static", StaticFiles(directory="static"), name="static")


@app.get("/")
def home():
    return {"message": "IoT Dashboard API Running"}


@app.get("/dashboard")
def dashboard():
    return FileResponse("static/index.html")


@app.post("/weather")
def add_weather(temperature: float, humidity: float):
    data = {
        "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
        "temperature": temperature,
        "humidity": humidity
    }
    db.insert(data)
    return {"status": "success", "data": data}


@app.get("/weather")
def get_weather():
    return db.all()
```
