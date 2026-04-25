# AegisPath: Rural Emergency Dispatch Engine
### *Bridging the "Data Gap" for Rapid Response in Underserved Regions*

![ArcGIS Pro](https://img.shields.io/badge/Platform-ArcGIS%20Pro%203.x-007AC2?style=flat&logo=arcgis&logoColor=white) 
![Python](https://img.shields.io/badge/Language-Python%203.9-3776AB?style=flat&logo=python&logoColor=white) 
![License](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey)

---

## 📌 Project Overview
In many rural regions of Bangladesh (Upazilas), global navigation platforms lack the granularity required for emergency services. "Kacha" roads and village paths are frequently missing from standard datasets, leading to critical delays. 

**AegisPath** is a Python-driven routing engine built within the ArcGIS Pro environment. It leverages a custom-digitized, high-fidelity road network to calculate the absolute quickest path from a mobile GPS coordinate to the nearest emergency facility.

---

## 🗺️ Data Source & Methodology
The accuracy of any routing engine depends entirely on its base map. 
* **Primary Source:** The road network for this project was meticulously digitized using **LGED (Local Government Engineering Department, Bangladesh)** maps as the authoritative ground truth.
* **Digitization Process:** Every segment was manually cross-referenced with high-resolution satellite imagery to ensure topological connectivity, particularly at rural intersections and bridge crossings that are often omitted in commercial maps.
* **Network Dataset (ND):** The data was transformed into a professional Network Dataset, incorporating travel modes, impedance attributes (length), and U-turn policies tailored for emergency vehicle maneuvers.

---

## ⚙️ Core Mechanisms
AegisPath isn't just a simple pathfinder; it includes professional GIS logic to ensure reliability in the field:

* **Automated Coordinate Projection:** The engine accepts raw **WGS84 (EPSG: 4326)** coordinates from mobile devices and automatically projects them into the local projected coordinate system of the road network to prevent spatial displacement errors.
* **Dynamic Search Tolerance:** In rural areas where an incident might occur far from a main road, the script employs a smart snapping algorithm that scans up to **5,000 meters** (adjustable) to find the nearest navigable road edge.
* **Modern `arcpy.nax` Implementation:** Unlike legacy scripts using the older `arcpy.na` module, AegisPath utilizes the modern **nax framework**, which offers superior performance, multithreaded solving, and cleaner output schemas.
* **In-Memory Volatility:** To ensure maximum speed and zero disk clutter for dispatchers, all intermediate point creation and processing occur in the `memory\` workspace.

---

## 🛠️ Tech Stack & Requirements
* **Software:** ArcGIS Pro (3.0 or higher recommended)
* **Extension:** ArcGIS Network Analyst
* **Language:** Python 3.x (ArcPy)
* **Symbology:** Custom `.lyrx` template for high-contrast visibility.

---

## 🚀 How to Use 
1. **Input Coordinates:** Enter the Longitude (X) and Latitude (Y) provided by the 999 caller.
2. **Select Facility:** Choose between Police Stations or Health Centers.
3. **Execute:** The tool snaps the point to the LGED-verified network and generates a neon-highlighted route.
4. **Result:** View the exact distance in Kilometers and the precise path to guide the driver.

---

## 🔒 Limitations & IP Protection
* **Logic vs. Data:** This repository contains the **Python Logic Engine** and **Symbology Templates**. 
* **Proprietary Data:** The high-fidelity LGED-digitized Geodatabase and Network Dataset are **not included** to protect intellectual property and the integrity of the institutional data.
* **Traffic:** Currently, the system uses static distance impedance. Future iterations plan to integrate travel-time decay based on road surface types (Paved vs. Kacha).

---

##  Screenshots
<img width="1920" height="1040" alt="Screenshot 2026-04-25 105937" src="https://github.com/user-attachments/assets/d43c29ad-57a9-4b28-a69a-6c45985539ab" />
<img width="1920" height="1040" alt="Screenshot 2026-04-25 110003" src="https://github.com/user-attachments/assets/391a0061-49b0-412b-8ba2-ef19712b38b2" />
<img width="1920" height="1040" alt="Screenshot 2026-04-25 110110" src="https://github.com/user-attachments/assets/78259d15-852c-412c-8d53-ebe6118b4392" />
<img width="1920" height="1040" alt="Screenshot 2026-04-25 110141" src="https://github.com/user-attachments/assets/03bea589-e0e7-4b10-bf75-93624e18dbd4" />


##  Screenshots


## 📧 Contact & Support
**Mustaq Hasnat Tamim** *Undergraduate Student* Department of Environmental Science and Geography  
Islamic University, Bangladesh  

📩 **Email:** [m.h.tamim.esg@std.iu.ac.bd](mailto:m.h.tamim.esg@std.iu.ac.bd)  
🔗 **LinkedIn:**   https://linkedin.com/in/mustaqhasnattamim
🌐 **GitHub:** https://github.com/mustaqhasnattamim
👥 **Facebook:** https://facebook.com/mustaqhasnattamim13

---

## 📜 Licensing
This project is shared under the **Creative Commons Attribution-NonCommercial-NoDerivs 4.0 International (CC BY-NC-ND 4.0)**. 

* **Attribution:** You must give appropriate credit.
* **Non-Commercial:** You may not use this material for commercial purposes.
* **No-Derivatives:** If you remix, transform, or build upon the material, you may not distribute the modified material.
