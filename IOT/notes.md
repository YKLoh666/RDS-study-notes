# Internet of Things

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
| Core Platform Layer     | Process IoT tasks that reach the cloud. Features include: Messaging Middleware (Device Management), Protocol Gateway, , Data Storage, and Data Aggregation & Filtering.                                            |
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
