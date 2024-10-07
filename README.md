# README: Smart Refrigerator IoT API Project

## **Project Name**: IoT Smart Refrigerator with Edge Computing

---

### **Overview**
This project demonstrates the creation of an **IoT-enabled Smart Refrigerator** using edge computing and cloud integration. The refrigerator monitors internal conditions like temperature, humidity, and inventory, processes the data locally for real-time adjustments, and sends important information to the cloud for storage, analytics, and alerting.

---

### **Key Features**
1. **Real-time Temperature & Humidity Monitoring**: Automatically adjusts cooling based on internal conditions and sends alerts if thresholds are exceeded.
2. **Inventory Management**: Tracks items inside the refrigerator, providing reminders when food is low or about to expire.
3. **Energy Monitoring**: Tracks power usage and optimizes energy consumption.
4. **Remote Control & Monitoring**: Users can adjust settings and monitor the refrigerator via a mobile app or web dashboard.
5. **Edge Computing**: Local processing for real-time responses, reducing reliance on cloud services.
6. **Cloud Analytics**: Historical data sent to the cloud for long-term storage, user behavior analysis, and system performance optimization.
7. **Predictive Maintenance**: Notifies users when components may need servicing.

---

### **Project Architecture**

#### 1. **Hardware Components**
- **Sensors**: Temperature, humidity, and weight sensors for monitoring.
- **Edge Device**: Microcontroller (like Raspberry Pi or ESP32) for local processing.
- **Wi-Fi Module**: Ensures cloud connectivity.
- **Cloud Services**: AWS IoT Core for data management and analytics.

---

#### 2. **API Design**

##### **A. Edge Device APIs**

1. **GET /temperature**
   - **Purpose**: Retrieve the current temperature.
   - **Response**:
     ```json
     {
       "temperature": 4.5,
       "unit": "Celsius",
       "timestamp": "2024-10-05T12:30:00Z"
     }
     ```

2. **GET /humidity**
   - **Purpose**: Retrieve the current humidity.
   - **Response**:
     ```json
     {
       "humidity": 55.2,
       "unit": "%",
       "timestamp": "2024-10-05T12:30:00Z"
     }
     ```

3. **GET /inventory**
   - **Purpose**: Retrieve a list of current inventory.
   - **Response**:
     ```json
     {
       "items": [
         {
           "name": "Milk",
           "quantity": 1,
           "unit": "L",
           "expiry_date": "2024-10-10"
         },
         {
           "name": "Eggs",
           "quantity": 6,
           "unit": "pieces",
           "expiry_date": "2024-10-12"
         }
       ]
     }
     ```

4. **POST /temperature**
   - **Purpose**: Adjust refrigerator temperature.
   - **Request Body**:
     ```json
     {
       "temperature": 4.0,
       "unit": "Celsius"
     }
     ```

5. **POST /power-savings-mode**
   - **Purpose**: Enable or disable power-saving mode.
   - **Request Body**:
     ```json
     {
       "mode": "on"
     }
     ```

---

##### **B. Cloud APIs**

1. **POST /send-data**
   - **Purpose**: Send sensor data to the cloud for storage and analytics.
   - **Request Body**:
     ```json
     {
       "device_id": "refrigerator-001",
       "temperature": 4.5,
       "humidity": 55.2,
       "power_usage": 150.0,
       "timestamp": "2024-10-05T12:35:00Z"
     }
     ```

2. **GET /alerts**
   - **Purpose**: Retrieve alerts related to system performance or conditions.
   - **Response**:
     ```json
     {
       "alerts": [
         {
           "type": "temperature",
           "message": "Temperature is higher than the desired setting",
           "severity": "high",
           "timestamp": "2024-10-05T12:36:00Z"
         },
         {
           "type": "inventory",
           "message": "Milk is about to expire",
           "severity": "medium",
           "timestamp": "2024-10-05T12:36:30Z"
         }
       ]
     }
     ```

---

### **Data Flow**

1. **Edge Device Operations**: 
   - Sensors collect data (temperature, humidity, inventory).
   - The edge device processes and adjusts local conditions in real-time.
   - Key actions like cooling and alerts are handled locally.

2. **Cloud Communication**: 
   - Periodic data (e.g., temperature, energy usage) is sent to the cloud for advanced analytics.
   - Cloud services generate alerts or recommendations for users.

---

### **Security**
- **OAuth 2.0**: Used for user authentication.
- **SSL/TLS Encryption**: All communications between edge and cloud are encrypted for security.

---

### **Example Scenarios**

1. **Check Temperature**:
   - The mobile app sends a `GET /temperature` request, and the system responds with the current temperature.

2. **Adjust Temperature**:
   - The user sends a `POST /temperature` request to lower the fridge’s temperature, and the system confirms the change.

3. **Send Data to Cloud**:
   - Every 10 minutes, sensor data is transmitted to the cloud.

4. **Receive Alerts**:
   - The user is alerted when the refrigerator’s internal temperature exceeds a certain threshold.

---

### **Conclusion**
The Smart Refrigerator API project integrates IoT and edge computing to deliver efficient, real-time management of refrigerator conditions while leveraging cloud-based analytics for monitoring and predictive maintenance. This project demonstrates the use of modern technologies like APIs, cloud, and IoT to create intelligent appliances.
