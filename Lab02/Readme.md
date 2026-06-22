# Lab 2: Developing and Deploying a REST API to Store Data on Cloud

## Objectives

1. Launch and configure an AWS EC2 instance  
2. Create a Python virtual environment (venv)  
3. Install FastAPI, Uvicorn, and TinyDB  
4. Develop REST API endpoints using FastAPI  
5. Store temperature and humidity data with timestamps  
6. Test GET and POST API endpoints  

---

# Background Theory

## Cloud Computing in IoT Systems

Cloud computing allows IoT devices to store, process, and access data over the internet instead of relying only on local storage. It provides scalability, reliability, and remote accessibility for IoT applications.

## AWS EC2 (Elastic Compute Cloud)

AWS EC2 is a cloud service provided by Amazon Web Services that allows users to create virtual servers in the cloud. It enables developers to deploy applications remotely and manage computing resources efficiently.

## REST API Architecture

REST (Representational State Transfer) API is a communication architecture that allows different applications to exchange data using HTTP methods such as GET, POST, PUT, and DELETE.

## FastAPI Framework

FastAPI is a modern Python web framework used for building APIs quickly and efficiently. It provides high performance and automatic API documentation.

## TinyDB Database

TinyDB is a lightweight document-oriented database written in Python. It stores data in JSON format and is suitable for small applications and IoT projects.

## HTTP GET and POST Methods

- **GET Method:** Used to retrieve data from the server.  
- **POST Method:** Used to send data to the server for storage or processing.  

---

# Procedure

## Step 1: Launch AWS EC2 Instance

1. Login to AWS Console.
2. Open EC2 Dashboard.
3. Launch a new Ubuntu instance.
4. Configure security groups and allow HTTP and SSH access.
5. Connect to the EC2 instance using SSH.
