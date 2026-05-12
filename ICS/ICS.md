# ICS Notes

- [ICS Notes](#ics-notes)
  - [Chapter 1: Introduction to Computer Security](#chapter-1-introduction-to-computer-security)
    - [Security Problems](#security-problems)
    - [Principles of Computer Security](#principles-of-computer-security)
    - [Vulnerabilities](#vulnerabilities)
    - [Threats vs Attacks](#threats-vs-attacks)
    - [Threat Actors](#threat-actors)
    - [Attack Categories](#attack-categories)
    - [Attack Types](#attack-types)
    - [Attack Vectors](#attack-vectors)
    - [New Targets of Attacks](#new-targets-of-attacks)
    - [New Strategies](#new-strategies)
  - [Chapter 2: Malicious Software](#chapter-2-malicious-software)
    - [Classification of Malware](#classification-of-malware)
      - [Snoop](#snoop)
      - [Launch](#launch)
      - [Imprison](#imprison)
      - [Deceive](#deceive)
      - [Evade](#evade)
    - [Countermeasures](#countermeasures)
  - [Chapter 3: Elementary Cryptography](#chapter-3-elementary-cryptography)
    - [Effective Cryptosystem](#effective-cryptosystem)
    - [Simple Ciphers](#simple-ciphers)
    - [Use Cases](#use-cases)
    - [Data States](#data-states)
    - [Cryptographic Algorithms](#cryptographic-algorithms)
      - [Symmetric Encryption](#symmetric-encryption)
      - [Asymmetric Encryption](#asymmetric-encryption)
      - [Hashing](#hashing)
      - [Authentication](#authentication)
    - [Cryptographic Attacks](#cryptographic-attacks)
      - [Algorithm Attacks](#algorithm-attacks)
      - [Collision Attacks](#collision-attacks)
    - [Quantum Cryptographic Defenses](#quantum-cryptographic-defenses)
    - [Applications of Cryptography](#applications-of-cryptography)
  - [Chapter 4: Authentication \& Access Control](#chapter-4-authentication--access-control)
    - [Means of Authentication](#means-of-authentication)
    - [Knowledge-Based - Passwords](#knowledge-based---passwords)
      - [Challenges](#challenges)
      - [Attacks](#attacks)
    - [Token-Based Authentication](#token-based-authentication)
    - [Biometric Authentication](#biometric-authentication)
    - [Authentication Tips](#authentication-tips)
    - [Access Control](#access-control)
    - [Access Control Process](#access-control-process)
    - [Access Control Policies](#access-control-policies)
  - [Chapter 5: Network Security](#chapter-5-network-security)
    - [Attacks on Networks](#attacks-on-networks)
    - [Network Security Components](#network-security-components)
    - [Types of Cloud](#types-of-cloud)
    - [Cloud Security Challenges](#cloud-security-challenges)
    - [Secure Cloud Computing](#secure-cloud-computing)
    - [Virtualisation Challenges](#virtualisation-challenges)
    - [Wireless Network Attacks](#wireless-network-attacks)
    - [Wireless Security Protocols](#wireless-security-protocols)
    - [Wireless Security Solutions](#wireless-security-solutions)
  - [Chapter 6: Physical Security](#chapter-6-physical-security)
    - [Categories of Physical Assets to Protect](#categories-of-physical-assets-to-protect)
    - [Physical Security Threats](#physical-security-threats)
    - [Security Control Measures](#security-control-measures)
      - [External Perimeter Defenses](#external-perimeter-defenses)
      - [Sensors](#sensors)
      - [Internal Controls](#internal-controls)
      - [Environmental Threat Controls](#environmental-threat-controls)
      - [Best Practices](#best-practices)
  - [Chapter 7: Risk Management and Data Privacy](#chapter-7-risk-management-and-data-privacy)
    - [Common Information Security Policies](#common-information-security-policies)
    - [Risk Types](#risk-types)
    - [Risk Analysis](#risk-analysis)
    - [Risk Management Strategies](#risk-management-strategies)
    - [Risk Management Control Types](#risk-management-control-types)
    - [Data Types](#data-types)
    - [Data Protection](#data-protection)
    - [Data Destruction](#data-destruction)
  - [Chapter 8: Incident Preparation, Response, and Investigation](#chapter-8-incident-preparation-response-and-investigation)
    - [Incident Preparation](#incident-preparation)
    - [Incident Response](#incident-response)
    - [Incident Investigation](#incident-investigation)

## Chapter 1: Introduction to Computer Security

### Security Problems

- Lack of security awareness among employees and users
- Lack of security mindset among IT professionals
- Insecure applications
- Misconfigurations
- Increasing number of insecure network devices (mobiles, IoT)
- Attack techniques are getting more sophisticated

### Principles of Computer Security

- **Confidentiality**: Only sender and recipient can access the message
- **Authentication**: Establish proof of identity
- **Integrity**: Ensure message is not altered during transmission
- **Non-repudiation**: Sender cannot deny sending the message
- **Availability**: Ensure services are available when needed
- **Access Control**: Restrict access to resources based on permissions (_Rule based_ for resource side, _Role based_ for user side, using _Access Control Lists_ or _Access Control Matrix_)

### Vulnerabilities

- **Platforms**: Legacy Platforms (No security updates), On-premises Platforms (inadequate security measures), Cloud Platforms (misconfigurations)
- **Configuration**: Default Settings, Open Ports & Services, Unsecured Root Accounts, Open Permissions, Unsecure Protocols, Weak Encryption, Human Errors
- **Third Parties**: Weakest Link Principle (Third-party vulnerabilities can compromise the main organization)
- **Patches**: Difficulty in applying firmware patches, Delayed in applying patches
- **Zero-Day**: Unknown vulnerabilities to vendor exploited by attackers before a patch is available

### Threats vs Attacks

- **Threat** is a potential dangerous event that have not yet occurred, while **Attack** is an realisation of a threat that have already caused damage to the system.

### Threat Actors

- **Script Kiddies**: Unskilled individuals using pre-made tools to exploit vulnerabilities
- **Hacktivists**: Motivated by ideology, e.g. DDOS attacks, website defacement
- **Nation-State Actors**: State-sponsored espionage, APTs (Advanced Persistent Threats), e.g. Social Engineering, RATs (Remote Access Trojans)
- **Insiders**: Financial gain or revenge, e.g. Data Theft, Sabotage
- **Cybercriminals**: Financially motivated, e.g. Ransomware, Phishing, Identity Theft

### Attack Categories

- **Interception**: Compromise confidentiality, e.g. Eavesdropping
- **Interruption**: Compromise availability, e.g. Denial of Service (DoS)
- **Modification**: Compromise integrity, e.g. Man-in-the-Middle (MitM)
- **Fabrication**: Compromise authenticity, e.g. Spoofing

### Attack Types

- **Passive Attacks**: Attack not affecting system resources, e.g. Eavesdropping, Traffic Analysis
- **Active Attacks**: Attack affecting system resources, e.g. DoS, MitM, Replay Attacks

### Attack Vectors

- **Email**: Phishing, Spear Phishing
- **Wireless**: Wi-Fi Attacks, Bluetooth Attacks
- **Removable Media**: USB Attacks
- **Direct Access**: Physical Access Attacks
- **Social Media**: Social Engineering Attacks
- **Supply Chain**: Malware injected into software or hardware during manufacturing or distribution
- **Cloud**: Misconfigurations, Insecure APIs, Data Breaches

### New Targets of Attacks

- **Critical Infrastructure**: Power grids, Water supply, Transportation systems
- **Higher Education**: Research data, Student records
- **Digital Assets & Online Gambling**: Financial data, Personal information
- **Supply Chain**: Software vulnerabilities, Hardware vulnerabilities
- **Mobile & IoT**: Personal data, Device control

### New Strategies

- **Assume Breach**: Strict policy, least privilege, network segmentation, monitoring
- **Artificial Intelligence**: Machine learning for threat detection, AI-powered attacks, less human effort

## Chapter 2: Malicious Software

### Classification of Malware

- **[Snoop](#snoop)**: Spies on user activities
- **[Launch](#launch)**: Infects system and spreads to other systems
- **[Imprison](#imprison)**: Prevents user from accessing system
- **[Deceive](#deceive)**: Hides its true, malicious intent
- **[Evade](#evade)**: Helps malware avoid detection by security software

#### Snoop

- **Spyware**: Tracking user activities without consent
- **Keyloggers**: Records keystrokes to capture sensitive information, can also capture screen and webcam
  - **Software Keyloggers**: Installed on the system, can be detected by antivirus
  - **Hardware Keyloggers**: Physical devices attached to keyboard, harder to detect, need physical access

#### Launch

- **Virus**: Replicates on same computer without user intervention, requires user action to spread
  - **File Based**: .EXE, .DOCX etc.; Appender, Split Infection, Mutation
  - **Fileless**: RAM-based; LOLBins (Living off the Land Binaries), e.g. PowerShell, WMI; write to registry
- **Worms**: Self-replicating, spreads across network without user intervention; consumes bandwidth, or can carry payloads (e.g. ransomware)
- **Bot & Botnet**: Spamming, DDoS, cryptomining; controlled by Command and Control (C&C) servers

#### Imprison

- **Ransomware**
- Type
  - **Blocker Ransomware**: Full-screen message blocking access
  - **Crypto Malware**: Encrypts files
- Tactics
  - **Urgency**: Time+, amount+
  - **Destruction**: Threaten to delete files
  - **Scope**: Extends to all networked devices
  - **Target**: State & local governments due to weaker security measures

#### Deceive

- **PUP (Potentially Unwanted Program)**: Legitimate software with hidden malicious features, e.g. adware, browser hijackers
- **Trojan**: Disguised as legitimate software, but performs malicious actions
- **RAT (Remote Access Trojan)**: Provides remote control to attacker, can be used for espionage, data theft, or as a backdoor

#### Evade

- **Backdoors**: Created for troubleshooting, but can be exploited by attackers; e.g. Remote Desktop Protocol (RDP), Telnet
- **Logic Bombs**: Triggered by specific conditions, e.g. date, user action
- **Rootkits**: Collection of tools to hide its and other malware's presence, access to admin privileges; monitor, create backdoors, alter log files

### Countermeasures

- **Security Policies**: Policy for handle threats for different aspects, e.g. Removable Media Policy, Software Installation Policy
- **Security Awareness Training**: Educate users about threats and safe practices, e.g. Phishing Awareness Training
- **MFA (Multi-Factor Authentication)**: use App-based, SMS-based is vulnerable to OTP interception
- **Antimalware and Spam Filters**: Install and keep updated, use different vendors for layered defense
- **Changing Default Policies**: Enforcing longer password histories, shorter password expiration, account lockout policies
- **Routine Vulnerability Scanning**: Regularly scan for vulnerabilities and apply patches

## Chapter 3: Elementary Cryptography

### Effective Cryptosystem

- **Reversible**: Decryption should be possible to unscramble the message
- **Secrecy & Length of Key**: Security should rely on the secrecy and length of the key, not the algorithm (Kerckhoffs's Principle)
- **Substantial Cryptanalysis**: Should be analysed thoroughly by experts for robustness

### Simple Ciphers

- **Caesar Cipher**: Shift letters by a fixed number
- **XOR Cipher**: Bitwise exclusive OR operation, can be easily broken if key is reused

### Use Cases

- **Confidentiality**
- **Authentication**
- **Integrity**
- **Non-repudiation**
- **Obfuscation**

### Data States

- **Data at Rest**
- **Data in Transit**
- **Data in Processing**

### Cryptographic Algorithms

- **[Symmetric Encryption](#symmetric-encryption)**
- **[Asymmetric Encryption](#asymmetric-encryption)**
- **[Hashing](#hashing)**
- **[Authentication](#authentication)**

#### Symmetric Encryption

- **Block Ciphers**
  - Pad plaintext to fixed size blocks
  - **DES (Data Encryption Standard)**: 64-bit block size, 56-bit key, vulnerable to brute-force attacks
  - **3DES (Triple DES)**: Applies DES three times, more secure but slower
  - **AES (Advanced Encryption Standard)**: 128-bit block size, key sizes of 128, 192, or 256 bits, widely used and secure; AES-n where n is the key size in bits
  - **RC5 (Rivest Cipher 5)**: Variable block size and key size, designed for fast software encryption, not widely used due to patents
  - **RC6 (Rivest Cipher 6)**: Successor to RC5, designed for AES competition, fixed block size of 128 bits
- **Stream Ciphers**
  - Encrypts data one bit or byte at a time, use keystream (pseudorandom stream of bits generated from a key and a nonce) and XOR with plaintext
  - **RC4**: Simple and fast, but now considered insecure

#### Asymmetric Encryption

- Public and private key pair
- **RSA (Rivest-Shamir-Adleman)**: First widely used public key algorithm, based on the difficulty of factoring products of 2 large prime numbers; TLS/SSL, VPNs, e-mail
- **ECC (Elliptic Curve Cryptography)**: Based on the mathematics of elliptic curves, offers same security with smaller key sizes than RSA; lower power consumption, ideal for mobile and IoT devices, blockchain
- **DSA (Digital Signature Algorithm)**: Standard for digital signatures; provide non-repudiation and integrity
- **Diffie-Hellman (DH) Key Exchange**: Share base and modulo, compute public keys using modular exponentiation, then compute shared secret

#### Hashing

- Create fixed-size digest, secure (one-way function), unique (collision resistance), original (cannot produce desired hash)
- **MD5 (Message Digest 5)**: 32-digit hex hash, vulnerable to collision attacks
- **SHA-1 (Secure Hash Algorithm 1)**: Not secure
- **SHA-2 (Secure Hash Algorithm 2)**: SHA-256, SHA-384, SHA-512; widely used and secure
- **SHA-3 (Secure Hash Algorithm 3)**: Designed to thwart attacks, different internal structure than SHA-2

#### Authentication

- **HMAC (Hash-based Message Authentication Code)**: The message is hashed and encrypted with the shared secret key, recipient can perform the same operation and compare results to verify integrity and authenticity

### Cryptographic Attacks

#### Algorithm Attacks

- **Known Ciphertext Attack**: analyze ciphertexts patterns
- **Downgrade Attack**: Force use of weaker algorithm
- **Misconfiguration**: Weak/Outdated algorithms

#### Collision Attacks

- **Birthday Attack**: Exploit the birthday paradox to find two different inputs that produce the same hash

### Quantum Cryptographic Defenses

- **Quantum Computing**: Use qubits which can superpose states, faster than classical computers for certain problems, e.g. Shor's algorithm can break RSA and ECC
- **Quantum Cryptography**: Use principles of quantum mechanics to secure communication, e.g. Quantum Key Distribution (QKD) using entangled particles
- **Post-Quantum Cryptography**: Develop algorithms resistant to quantum attacks, e.g. lattice-based cryptography, hash-based signatures

### Applications of Cryptography

- **Software Based Cryptography**: File & File System Cryptography, Full Disk Encryption (FDE) like BitLocker
- **Hardware Encryption**: USB Devices, Self-Encrypting Drives (SEDs), Hardware Security Modules (HSMs), Trusted Platform Modules (TPMs)
- **Blockchain**: Shared, temper-resistant digital ledger to record transactions, consensus mechanisms

## Chapter 4: Authentication & Access Control

- RFC 4949 Definition: Process of verifying identity claimed by or for a system entity
- Identification, Verification

### Means of Authentication

| Type               | Description          | Examples                                    |
| ------------------ | -------------------- | ------------------------------------------- |
| Something You Know | Knowledge-based      | Password, PIN, Security Questions           |
| Something You Have | Token-based          | Smart Card, Security Key                    |
| Something You Are  | Static Biometric     | Fingerprint, Facial Recognition, Iris Scan  |
| Somewhere You Do   | Behavioral Biometric | Keystroke, Gait Analysis, Voice Recognition |

### Knowledge-Based - Passwords

#### Challenges

- Hard to memorise long, complex passwords, and unique passwords for each account
- Security policies (expiration, history) can lead to weaker passwords
- Weak passwords
- Reuse of passwords across multiple accounts
- Predictable password patterns (Appending, Replacing)

#### Attacks

- **Pass the Hash**: Directly use the hash of a stolen password
- **Password Cracker**: Hashing potential passwords and comparing with stolen hashes
- **Password Spraying**: Try common passwords across many accounts to avoid lockout
- **Brute Force Attack**: Try all possible combinations
- **Rule Attack**: Create mask for password patterns, e.g. ?l?l?l?d?d for 3 lowercase letters followed by 2 digits
- **Dictionary Attack**: Use a list of common passwords and variations
- **Rainbow Table Attack**: Precompute hashes for common passwords and store in a table for quick lookup
- **Password Collections**: Use leaked password from data breaches as candidates

### Token-Based Authentication

- Specialised Devices
  - **Smart Cards**: Plastic card with embedded chip, but requires special readers, vulnerable to cloning; e.g. Credit Cards
  - **Windowed Tokens**: Small device showing OTP, must manually enter OTP quickly; e.g. Time-based OTP (refresh periodically), HMAC-based OTP (key in PIN to get OTP, event-based)
- Smartphones
  - **Phone Calls**
  - **SMS Message Text**: Vulnerable to SIM swapping and interception
  - **App-Based**: Can be targeted by malware
- Security Keys
  - Hardware dongle contains cryptographic
  - Burn into the device
  - Very secure, but can be lost or stolen

### Biometric Authentication

- Physiological
  - Specialised
    - **Retinal**
    - **Fingerprint**
    - **Vein Pattern**
  - Standard (Using hardware already present in devices)
    - **Facial Recognition**
    - **Iris Scan**
- Cognitive
  - **Windows Picture Password**
  - **Memorable Events**
- Behavioral
  - **Keystroke Dynamics**: Dwell time, Flight time
  - **Gait Analysis**
  - **Voice Recognition**

### Authentication Tips

| Tips                    | Description                                                                                                                                                                        |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Protect password digest | Use salts to prevent rainbow table attacks, use key stretching to increase time for brute-force attacks, use lockout policies to prevent password spraying and brute-force attacks |
| Password Safety         | Use long passwords instead of complex ones, use password vaults to generate and store unique passwords, use password keys (hardware-based devices)                                 |
| Secure Technology       | SSO (Single Sign-On), Authentication Services (Kerberos)                                                                                                                           |

### Access Control

- NIST Definition: Process of granting or denying specific requests to obtain and use information and related services, or to enter physical facilities
- RFC 4949 Definition: Process by which use of system resources is regulated according to a security policy and is permitted only by authorised entities

### Access Control Process

- **Authentication**
- **Authorization**: Check Authorization Database for permission
- **Auditing**

### Access Control Policies

- **DAC (Discretionary Access Control)**: Owner controlled, based on user identity and access rules, e.g. ACL or ACM
- **MAC (Mandatory Access Control)**: System controlled, based on resource's security label and user's security clearance, more secure, defense against Trojan horses
- **RBAC (Role-Based Access Control)**: Access based on user's role, simplifies management, but can lead to role explosion
- **ABAC (Attribute-Based Access Control)**: Access based on attributes of user, resource, and environment, more flexible but complex to manage; Attributes categories: Subject, Action, Object, Environment

## Chapter 5: Network Security

### Attacks on Networks

- **Network Packet Sniffer**: Put network adapter card in promiscuous mode to capture all traffic
- **IP Spoofing & DoS Attack**: Spoof as trusted source to bypass access control, send TCP SYN packets without completing handshake to consume resources
- **Password Attack**
- **Data Exfiltration**: Send sensitive data to external location
- **MITM (Man-in-the-Middle) Attack**: Intercept and modify communication between two parties, e.g. ARP Spoofing, DNS Spoofing, DoS, Session Hijacking, Eavesdropping

### Network Security Components

- **Malware Scanner**: Signature-based (Email, Download, File Scanning), Behavior-based (heuristic), Sandboxing, Machine Learning
- **Firewalls**: Barrier between trusted and untrusted networks; Cannot block all attacks (user downloaded Trojans, internal threats), Stateless Packet Filtering, Stateful Packet Inspection, Application Gateway (Proxy)
- **Antispyware**
- **Intrusion Detection System (IDS)**: Passive, monitoring, alert administrators
- **Intrusion Prevention System (IPS)**: Active, shutdown suspicious communication, risk of false positives
- **Digital Certificates**: X.509, signed by trusted Certificate Authority (CA), used in TLS/SSL for secure communication
- **SSL/TLS (Secure Sockets Layer/Transport Layer Security)**: Encrypts communication
- **VPN (Virtual Private Network)**: Virtual encrypted tunnel over the internet, emulates a direct connection

### Types of Cloud

- NIST Definition: Model for enabling convenient, on-demand network access to a shared pool of configurable computing resources that can be rapidly provisioned and released with minimal management effort
- **Public Cloud**: Services and infrastructure offered to all users
- **Community Cloud**: Specific organisations with shared concerns, e.g. government agencies
- **Private Cloud**: Exclusive and managed within private network, more control and security, but higher cost
- **Hybrid Cloud**: Flexible

### Cloud Security Challenges

- **Unauthorised Access**
- **Lack of Visibility**: Limited insight into cloud provider's security measures and practices
- **Insecure API**
- **Compliance Regulations**: Impact of no visibility
- **System Vulnerabilities**

### Secure Cloud Computing

- Duplicate processes to different regions
- Use microservices architecture, use secret manager manage secrets across microservices
- Functional Area Mitigation
  - Storage: Access control, Encryption
  - Network: VPN, Private/Public Subnetting
  - Compute: Security Groups, Dynamic Resource Allocation

### Virtualisation Challenges

- Host Virtualisation is hypervisor of multiple virtual machines (VMs) on a single physical host
- **Requires Virtualisation-Aware Security Tools**
- **Need protect from external network and VMs on the same host**
- **VM Escape**: Attacker breaks out of VM to access host or other VMs, e.g. Hypervisor Vulnerabilities

### Wireless Network Attacks

- Bluetooth
  - **Bluejacking**: Send unsolicited messages
  - **Bluesnarfing**: Access data without consent
- NFC
  - **Eavesdropping**
  - **Data Theft**
  - **MITM**
  - **Device Theft**
- RFID
  - **Unauthorised Scanning**
  - **Fake Tags**
  - **Eavesdropping**
- WLAN
  - **Rogue Access Point**: Unauthorised AP bypassing security
  - **Evil Twin**: Fake AP mimicking authorised AP to trick users into connecting
  - **Intercepting Wireless Data**: Capture RF signals from open or misconfigured AP
  - **Wireless DoS**: Flood AP with traffic to disrupt service

### Wireless Security Protocols

- WEP
- WPA
- WPA2
- WPA3

### Wireless Security Solutions

- **Access Control**: MAC Address Filtering
- **Encryption**: Use WPA3 or WPA2
- **Site Survey**: Check coverage, bandwidth, and security

## Chapter 6: Physical Security

### Categories of Physical Assets to Protect

- **Info System Hardware**
- **Physical Facilities**: Buildings
- **Supporting Facilities**: Electricity, communication services, HVAC
- **Personnel**: Employees

### Physical Security Threats

- **Unauthorised Access to Premises**
- **Theft**
- **Vandalism**
- **Fire**
- **Unstable Power Supply**
- **Humidity**
- **Lightning**
- **Floods**
- **Earthquakes**

### Security Control Measures

- **[External Perimeter Defenses](#external-perimeter-defenses)**: Restrict access to the premises
- **[Sensors](#sensors)**: Detect intrusions and environmental conditions
- **[Internal Controls](#internal-controls)**: Activates when external defenses are breached
- **[Environmental Threat Controls](#environmental-threat-controls)**: Protect against environmental threats
- **[Best Practices](#best-practices)**

#### External Perimeter Defenses

- **Passive Barriers**: Fences (Tall, Signage), Lighting (For monitoring)
- **Active Security Personnel**: Human guards who patrol the premises, CCTV
- **Sensors**: Trigger alarms when breached

#### Sensors

- **Motion Sensors**: Infrared
- **Noise Sensors**: Microphones
- **Temperature Sensors**: Thermal cameras (Detect human)
- **Proximity Sensors**: Infrared, Electromagnetic

#### Internal Controls

- **Physical Locks**: Keys are given to only authorised personnel
- **Mantraps**: Two sets of interlocking doors, only one can be open at a time

#### Environmental Threat Controls

- **Fire Suppression Systems**: Gas-based
- **Voltage Controller**: Protect against power surges and outages
- **Air Conditioning**: Maintain optimal temperature and humidity for equipment
- **Lightning Rods**: Protect against lightning strikes
- **Flood Barriers & High Ground**: Protect against floods
- **Earthquake-Resistant Design**: Structural reinforcements to withstand earthquakes

#### Best Practices

- Data Center
  - Key given to those who need access only
  - Multilayer authentication (password + RFID card + biometric)
  - Server room logs
  - Encrypt all data
  - Redundant data stored fireproof offsite
  - Automated emergency response systems
- Workstations
  - Engrave identifying marks
  - Routinely inventory and audit
  - Physical Tethering (use cables)

## Chapter 7: Risk Management and Data Privacy

### Common Information Security Policies

- **Network Security Policy**: Network access control, architecture, security measures
- **Workstation Policy**: Antivirus, lock screen, password, updates
- **Acceptable Use Policy (AUP)**: Define acceptable and unacceptable use of channels (e.g. Internet, Email, Social Networks, File Transfer) for confidential information
- **Clean Desk Policy**: Free of sensitive notes or documents to prevent visual theft
- **Remote Access Policy**: Define requirements for remote access, e.g. VPN, devices
- **Password Policy**: Strong password creation, protection, and expiration
- **Account Management Policy**: Creation, administration, use and removal of user accounts
- **Email Security Policy**: Sending, receiving, and storage of email
- **Log Management Policy**: Log collection guidelines, compliance and retention
- **Security Incident Management Policy**: Requirements for reporting and responding, e.g. identification and mitigation
- **BYOD (Bring Your Own Device) Policy**: Restrictions and requirements
- **Patch Management Policy**: Apply patches to remove vulnerabilities
- **Server Security Policy**: Configuration
- **System Monitoring and Auditing Policy**: Real-time monitoring and after-the-fact auditing

### Risk Types

- Risk is chance of compromising an asset
- **Internal**: Insider threats, human error, misconfigurations
- **External**: Hacktivists, Cybercriminals
- **Legacy Systems**: No security updates
- **Multiparty**: Third-party vulnerabilities can compromise the main organisation
- **Intellectual Property**: Theft of trade secrets, patents, copyrights
- **Software Compliance & Licensing**: Unlicensed software, violation of licensing agreements

### Risk Analysis

- **Qualitative Risk Assessment**: Label risks as High, Medium, Low based on observation
- **Quantitative Risk Assessment**: Assign monetary value to risks
- Single Loss Expectancy (SLE) = Asset Value (AV) x Exposure Factor (EF)
- Annuallized Loss Expectancy (ALE) = SLE x Annual Rate of Occurrence (ARO)
- **Risk Register**: Document listing identified risks, their severity, and mitigation strategies

### Risk Management Strategies

- **Risk Acceptance**: Acknowledge risk and take no action, e.g. low-risk vulnerabilities
- **Risk Transference**: Shift risk to a third party, e.g. insurance, outsourcing
- **Risk Avoidance**: Eliminate risk by not engaging in the activity, e.g. not using a vulnerable software
- **Risk Mitigation**: Implement controls to reduce risk, e.g. firewalls, encryption

### Risk Management Control Types

- **Deterrent**: Discourage security violations, e.g. Warning Signs of CCTV
- **Preventive**: Prevent threats from contacting the vulnerabilities, e.g. Awareness Training
- **Physical**: Prevent physical access, e.g. Locks, Fences
- **Detective**: Identify and react to security violations, e.g. Intrusion Detection Systems (IDS), sensors
- **Compensating**: Alternative controls when primary controls are not feasible, e.g. Isolating infected systems on a separate network if patching is not possible
- **Corrective**: Mitigate damage after a security incident, e.g. Clean up malware after an infection, restore from backup after data loss

### Data Types

- **Confidential**: Highest level of sensitivity (Handle by users with highest pre-approved authentication)
- **Private**: Restricted access, medium sensitivity (Handle by users with need-to-know basis)
- **Sensitive**: Can cause catastrophic damage if disclosed (Restricted to employees with business need)
- **Critical**: Availability needs, unavailability impacts function (Rigorous protection)
- **Proprietary**: Belongs to enterprise (Available to any current employee or contractor)
- **Public**: No restrictions (Available to anyone)
- **Personal Identifiable Information (PII)**: Can identify an individual, e.g. Name, Address, Social Security Number (Kept secure to prevent identity theft)
- **Protected Health Information (PHI)**: Medical information, e.g. Medical history, Test results (Protected under HIPAA)

### Data Protection

- **Impact Assessment**: Measure protection effectiveness
- **Privacy Notice**: Inform users about data collection and usage
- **Terms of Agreement**: Protect against legal liability
- **Data Minimisation**: Collect only necessary data
- **Data Masking**: Hide sensitive data with modified content
- **Tokenisation**: Replace sensitive data with non-sensitive tokens
- **Data Sovereignty**: Country specific regulations on data storage and processing

### Data Destruction

- **Paper Media Destruction**: Burn, Shred, Pulp
- **Electronic Media Destruction**: Degaussing (Disrupt magnetic fields), Wiping (Overwrite data), Physical Destruction (Shredding, Crushing, Melting)

## Chapter 8: Incident Preparation, Response, and Investigation

### Incident Preparation

- **Create an IRP (Incident Response Plan)**
  - **Preparation**: Equipping employees to handle potential incidents
  - **Identification**
  - **Containment**: Isolate affected systems to prevent spread
  - **Eradication**: Remove threat from the environment
  - **Recovery**: Restore systems to normal operation
  - **Lessons Learned**: Analyze incident to improve future response
- **Perform Exercises**
  - **Tabletop**: Discussion-based, informal
  - **Walkthrough**: Step-by-step, more formal
  - **Simulation**: Realistic, high-pressure, tests actual response capabilities
- **Study Attack Frameworks**
  - **MITRE ATT&CK**
  - **Diamond Model of Intrusion Analysis**
  - **Cyber Kill Chain**

### Incident Response

- **SOAR (Security Orchestration, Automation, and Response) Playbooks and Runbooks**
  - **Playbook**: Linear checklist for specific incident types (What to do)
  - **Runbook**: Series of automated conditional steps (How to do it)
- **Perform Containment**
  - Network segmentation based on zero-trust principles
  - Isolate affected systems, e.g. disconnect from network
- **Make Configuration Changes**
  - Firewall rules
  - Content/URL filtering
  - Digital certificates
  - Data loss prevention (DLP) policies
  - Mobile Device Management (MDM) policies

### Incident Investigation

- **Data Sources**
  - **Log Files**
    - **Network-based Device Logs**: Firewall, router, switch logs
    - **System Logs**: Authentication server system logs
    - **Application Logs**: Software dump logs
    - **Voice and video communication Logs**: VoIP log files
  - **IP Monitors**
  - **Metadata**: Of files, web, mobile, email
  - **Analyzers**: Bandwidth monitor, protocol analyzer etc.
  - **Vulnerability Scanners**: Real-time monitoring for vulnerabilities
- **Digital Forensics**
  - **Secure the Scene**: Preserve evidence and prevent contamination
  - **Preserve the Evidence**: Create bit-by-bit copy of digital evidence, maintain chain of custody
  - **Document Chain of Custody**: Record of document handling
  - **Examine for Evidence**: Follow **order of volatility** to preserve fragile data first (Cache, RAM, Hard Drive)
