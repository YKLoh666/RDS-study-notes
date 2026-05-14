# Internet of Things

- [Internet of Things](#internet-of-things)
  - [Core elements of IoT](#core-elements-of-iot)
  - [Communication Models](#communication-models)
  - [Resources and Activities](#resources-and-activities)
  - [Porter's Five Forces](#porters-five-forces)
  - [Customers' Benefits](#customers-benefits)
  - [IoT Stacks](#iot-stacks)
  - [IoT Platform Architecture Components](#iot-platform-architecture-components)
  - [Ultrasonic Sensor](#ultrasonic-sensor)
  - [Firebase Realtime Database](#firebase-realtime-database)
  - [Arduino IDE](#arduino-ide)
  - [Trend, Challenges and Ethical Issues](#trend-challenges-and-ethical-issues)
  - [Inter-Intergrated Circuit (I2C)](#inter-intergrated-circuit-i2c)
  - [Smart Farming Solution](#smart-farming-solution)
  - [Humanoid Robots](#humanoid-robots)

## Core elements of IoT

| Element       | Real-World Example                                                             |
| ------------- | ------------------------------------------------------------------------------ |
| Identity      | Using serial numbers, IP addresses, or RFID tags to uniquely identify devices. |
| Intelligence  | Smart thermostats that learn user preferences and adjust settings accordingly. |
| Communication | Smart home devices communicating with each other via Wi-Fi or Bluetooth.       |

## Communication Models

| Model                       | Description                                                                                        |
| --------------------------- | -------------------------------------------------------------------------------------------------- |
| Device-to-Device (D2D)      | Direct communication between devices without intermediaries.                                       |
| Device-to-Gateway (D2G)     | Devices communicate with a central gateway that processes and forwards data.                       |
| Device-to-Cloud (D2C)       | Devices send data to cloud servers for storage and analysis.                                       |
| Back-End Data-Sharing (BDS) | Interoperability between different cloud services and platforms for data combination and analysis. |

## Resources and Activities

| Resource/Activity                     | Description                                                                                                                                                   |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unique Dataset                        | Using IoT to build dataset not available to competitors, such as Google collecting large amounts of data from its users which can be used for AI development. |
| Analytics                             | Superior algorithms to automate and optimize processes, such as Google algorithm to index World Wide Web.                                                     |
| Exclusive co-operations and contracts | Possible to strategically lockout competitors by securing exclusive partnerships with key players in the ecosystem.                                           |
| Talent Access                         | Create demand for talents, since IoT is a multidisciplinary field (e.g., engineering, data science, cybersecurity)                                            |
| IoT-Device / Product Development      | Mastering new technologies can decrease time to market and increase product differentiation                                                                   |
| Algorithm Development                 | Innovate and develop algorithms that are ahead of competitors                                                                                                 |

## Porter's Five Forces

| Force                              | How it influences IoT ecosystem                                                                                                                                                                                                     |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bargaining Power of Suppliers      | Suppliers of key components (sensors, chips) have high influence on pricing due to limited alternatives. This can lead to increased costs for IoT device manufacturers.                                                             |
| Bargaining Power of Buyers         | Buyers (consumers and businesses) have significant influence due to the increasing number of solutions available, driving demand for better features and lower prices. This forces company to innovate and improve their offerings. |
| Threat of New Entrants             | Low-cost hardware and open-source platforms lower barriers to entry, allowing new companies to enter the market. Expertise in security and scalability creates barriers for new entrants.                                           |
| Threat of Substitutes              | IoT solutions can substitute traditional methods of monitoring and control (e.g., manual processes, non-connected devices). The convenience and efficiency of IoT can make substitutes less attractive.                             |
| Rivalry Among Existing Competitors | Intense competition among established players (e.g., Google, Amazon, Microsoft) and startups drives innovation but can lead to price wars and reduced profit margins.                                                               |

## Customers' Benefits

Functional Product Benefits

| Category            | Customer Value                            |
| ------------------- | ----------------------------------------- |
| Daily Operations    | Monitoring, Localization, Control, Safety |
| Optimization        | Functionality, Convenience, Cost          |
| Maintenance/Service | Availability, Cost                        |

Functional Process Benefits

| Category              | Customer Value                                                              |
| --------------------- | --------------------------------------------------------------------------- |
| Strategic Information | Choice of machines, Sales optimization                                      |
| Daily Operations      | Monitoring, Control, Billing, Documentation, Contract Management, Usability |
| Optimization          | Availability, Quality, Automation, Costs                                    |

Functional Business Benefits

| Category            | Customer Value                                                                                    |
| ------------------- | ------------------------------------------------------------------------------------------------- |
| Customers           | Customer Retention, Customer Satisfaction, Lead Generation, Offer Optimization, Sales Proposition |
| Products            | Requirement Management                                                                            |
| New markets         | Data as a Product, IoT as Catalyst                                                                |
| New business models | New Services, Pay-per-use, Contracting                                                            |

Emotional Benefits (Maslow's Hierarchy of Needs)

| Category           | Customer Value                                                          |
| ------------------ | ----------------------------------------------------------------------- |
| Safety             | Security of body, Employment, Health, Property                          |
| Love/Belonging     | Friendship, Intimacy, Family                                            |
| Esteem             | Self-esteem, Confidence, Achievement, Respect                           |
| Self-Actualization | Creativity, Morality, Spontaneity, Problem-solving, Acceptance of facts |

## IoT Stacks

| Layer                   | Description                                                                                                                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Solution Layer          | The top layer that provides the end-user interface and experience. It includes applications and services that utilize IoT data to deliver value to customers.                                                      |
| Analysis Platform Layer | Orchestrates based on availability of cloud, fog and network resources. Has direct access to raw data and perform machine learning and data analytics. It also supplies authentication and authorization services. |
| Core Platform Layer     | Process IoT tasks that reach the cloud. Features include: Messaging Middleware (Device Management), Protocol Gateway, Data Storage, and Data Aggregation & Filtering.                                              |
| Communication Layer     | Utilises devices for communicating between devices and the cloud. Consists of various communication protocols (e.g., MQTT, CoAP, HTTP) and network technologies (e.g., Wi-Fi, Bluetooth, Zigbee).                  |
| Device Layer            | The bottom layer that consists of the actual IoT devices and sensors that collect and transmit data. Sensors, actuators, indicators, and embedded systems (controllers) are part of this layer.                    |

## IoT Platform Architecture Components

| Component                      | Description                                                                                                              |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| Connectivity and Normalisation | Ensure constant object connectivity and harmonise data formats for seamless communication between devices and platforms. |
| Device Management              | Manage device status, remote software deployment and updates                                                             |
| Processing & Action Management | Rule engine to trigger real time actions based on sensor data                                                            |
| Data Visualisation             | Graphical depiction of sensor data                                                                                       |
| Analytics                      | Advanced calculations and machine learning                                                                               |
| Additional Tools               | Development tools such as prototyping, access management and reporting                                                   |
| External Interfaces            | APIs, SDKs and gateways for integration with third-party applications such as ERP and CRM systems                        |
| Database                       | Repository for storing and managing data generated by IoT devices                                                        |

## Ultrasonic Sensor

- Used for distance measurement by emitting ultrasonic waves and measuring the time it takes for the echo to return.
- **Use cases**: Object detection, obstacle avoidance in robotics, parking assistance

```c
#define TRIG_PIN 23 // Pin connected to the trigger pin of the ultrasonic sensor
#define ECHO_PIN 22 // Pin connected to the echo pin of the ultrasonic sensor

void setup() {
    Serial.begin(115200);
    pinMode(TRIG_PIN, OUTPUT);
    pinMode(ECHO_PIN, INPUT);
}

void readUltrasonic() {
    digitalWrite(TRIG_PIN, HIGH);
    delayMicroseconds(10);
    digitalWrite(TRIG_PIN, LOW);

    float duration = pulseIn(ECHO_PIN, HIGH);

    float distance_cm = 0.034 * duration / 2; // Calculate distance in cm by multiplying duration by speed of sound (0.034 cm/µs) and dividing by 2 (round trip)
}
```

## Firebase Realtime Database

- A cloud-hosted NoSQL database that allows real-time data synchronization between clients and the server.

```c
#define FIREBASE_HOST "your-project-id.firebaseio.com"
#define FIREBASE_AUTH "your-database-secret"

FirebaseData firebaseData;

void setup() {
    Serial.begin(115200);
    
    // Connect wifi
    WiFi.begin("your-ssid", "your-password");

    Firebase.begin(FIREBASE_HOST, FIREBASE_AUTH);
    Firebase.reconnectWiFi(true);

    bool success;

    // Write data to Firebase
    success = Firebase.setFloat(firebaseData, "/sensor/distance", distance_cm);
    success = Firebase.setString(firebaseData, "/sensor/status", "active");
    success = Firebase.setInt(firebaseData, "/sensor/count", 10);

    // Read data from Firebase
    if (Firebase.getFloat(firebaseData, "/sensor/distance")) {
        if (firebaseData.dataType() == "float") {
            float distance = firebaseData.floatData();
            Serial.print("Distance: ");
            Serial.println(distance);
        }
    }
}
```

## Arduino IDE

- Key Considerations when writing code:
  - **Non-blocking code**: Avoid long delays or blocking operations in `loop()`. Use timers, interrupts or task scheduling to maintain responsiveness.
  - **Global variables**: Use global variables so both `setup()` and `loop()` can access it.

## Trend, Challenges and Ethical Issues

| Issue                                  | Description                                                                                                                     |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Ubiquity, omnipresence                 | IoT devices are everywhere at anytime, making it impossible to avoid them, raising concerns about privacy and data security.    |
| Miniaturisation, invisibility          | Smaller devices can be easily hidden, raising concerns about surveillance and unauthorized data collection.                     |
| Ambiguity                              | Boundary between natural and artificial beings is blurred, accountability issues arise when devices make autonomous decisions.  |
| Difficult identification               | Huge number of devices, difficult tracking, prone to security breaches and unauthorized access.                                 |
| Ultra-connectivity                     | Increased connectivity leads to more attack vectors, data can be intercepted and maliciously used.                              |
| Autonomous and unpredictable behaviour | Smart devices can make decisions based on human events, may lead to unexpected behaviour and ethical dilemmas.                  |
| Incorporated intelligence              | Human over reliance on smart devices can lead to loss of critical thinking and problem-solving skills.                          |
| Difficult control                      | Decentralised nature of IoT makes it difficult to control and monitor, may overlook malicious activities and security breaches. |

## Inter-Intergrated Circuit (I2C)

- SDA(Serial Data Line): Carries data between devices.
- SCL(Serial Clock Line): Synchronizes data transfer between devices.
- Supports multiple devices on the same bus, each with a unique address.
- If connecting multiple displays with the same address, they will conflict due to multiple devices acknowledging and cause data corruption.

## Smart Farming Solution

IPO Model:

- **Input**: Temperature sensors, camera, air humidity sensors, pH sensors, NPK sensors
- **Process**: Raspberry Pi
- **Output**: Nutrient dispenser, sprinkler system

Use cases for each layer of the IoT stack:

| Layer                   | Use Case                                                                                                                                                                                                             |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Solution Layer          | Mobile app for farmers to monitor soil moisture, temperature, and receive alerts. Remote control of irrigation systems.                                                                                              |
| Analysis Platform Layer | Data analytics to predict optimal watering schedules based on weather forecasts and historical data. Machine learning for pest detection using camera images.                                                        |
| Core Platform Layer     | Data storage for sensor readings, device management for connected sensors and actuators, data aggregation to combine sensor data for comprehensive analysis.                                                         |
| Communication Layer     | Use of MQTT protocol for efficient communication between sensors and cloud. Wi-Fi connectivity for remote access.                                                                                                    |
| Device Layer            | Soil moisture sensors to measure water content in soil. Temperature sensors to monitor ambient conditions. Camera for pest detection. Air humidity sensors for microclimate monitoring. pH sensors for soil acidity. |

## Humanoid Robots

- **Feasibility Study**
  - **General market opportunities**: Healthcare (elderly care, rehabilitation), Manufacturing (assembly line, hazardous environments), growing demand as they can perform tasks that are dangerous or require precision, and can operate 24/7 without fatigue.
  - **Time to market**: Key technologies such as AI, sensors and edge computing are yet to mature, it may impact the development timeline and increase costs.
  - **Channels to market**: Direct sales to businesses, partnerships with healthcare providers, online platforms for consumer sales.
- **Usage Viewpoint**
  - **Event**: User commands, sensor inputs, system alerts
  - **Stakeholders**: Operators, end-users
  - **User Interface**: Button, hand gestures, voice commands, mobile app
  - **Processes**: VR control, Remote monitoring, Movement
  - **Rules**: Safety protocols, Ethical guidelines
  - **Data**: Sensor data (proximity, force, temperature), User input data (commands, feedback), Operational data (battery status, performance metrics)
  - **Benefits/Goals**: Reduce labour costs, Increase uptime, Enhance precision, Improve safety
- **Platform Architecture Components**
  - **Processing & Action Management**: Humanoid robots uses AI algorithms to process sensor data and make real-time decisions for movement and task execution, such as balancing and navigation.
  - **Analytics**: Analyse the performance of the robot, identify areas for improvement and predict maintenance needs based on sensor data and operational metrics.
- **Issue: Autonomous and unpredictable behaviour**: Humanoid robots processing is almost black box due to the complexity of AI algorithms, it may lead to unexpected behaviour and ethical dilemmas when encountering real world events with undeterministic nature. For example, two humanoid robots may collide with each other when navigating a crowded environment, it may cause safety concerns and ethical dilemmas on how to program the robots to prioritise safety and make ethical decisions in such scenarios.