# QA Process  
## Agritech_BeeSense – Alpha  
### Termohygrometer – MiniBrain V0.1  
Version: 0.1.0  

---

# 1. General Information

| Field | Value |
|-------|--------|
| Repository | Agritech_BeeSense - Alpha |
| Branch | dev |
| Board | MiniBrain V0.1 |
| Project | Termohygrometer |
| Client | The World |
| Firmware Lead | isa@sense-ai.co |
| Hardware Lead | ana@sense-ai.co |
| Dev QA Team | daniel@sense-ai.co <br> mateo@sense-ai.co <br> cristian@sense-ai.co |
| Status | Not Started |
| Init Date | 16/02/2026 |
| Finish Date | TBD |

---

# 2. Reference Documentation

- Product Datasheet  
- User Manual  
- User Required Functionalities  
- Architecture Diagram  
- Technical Specifications  

---

# 3. Objective

Ensure that the Termohidrómetro Device meets product datasheet specifications, user manual  and user-required functionalities, guaranteeing correct operation, connectivity, data integrity, remote manageability, and long-term reliability.							
							 

---

# 4. Scope of QA

## 4.1 In Scope

- Firmware behavior validation  
- Hardware-functional validation  
- Sensor accuracy validation  
- Communication flows (BLE, WiFi, AWS)  
- Data storage & retransmission  
- OTA behavior  
- Alarm system validation  
- Security validation  

## 4.2 Out of Scope

- Mobile application UI testing  
- Cloud backend performance testing  
- Hardware manufacturing defects  

QA validates device behavior interacting with cloud/app, but not the cloud/app itself.

---

# 5. Requirement Traceability Matrix (RTM)

| Requirement ID | Description | Source | Priority | Test Case ID | Status |
|---------------|------------|--------|----------|--------------|--------|
| FR-01 | Device wakes up via timer correctly | Tech Specs | High | TC-01 | Pending |
| FR-02 | Reed short press triggers normal cycle | User Req | High | TC-02 | Pending |
| FR-03 | Reed long press activates BLE mode | User Req | High | TC-03 | Pending |
| FR-04 | Temperature measurement accuracy ±0.5°C | Datasheet | High | TC-10 | Pending |
| FR-05 | Humidity accuracy ±3% RH | Datasheet | High | TC-11 | Pending |
| FR-06 | Device reconnects to WiFi automatically | Tech Specs | High | TC-20 | Pending |
| FR-07 | Offline data stored and retransmitted | Tech Specs | High | TC-25 | Pending |
| FR-08 | OTA allowed only above safe battery threshold | Firmware Req | High | TC-30 | Pending |
| FR-09 | LED indicators reflect system state | User Manual | Medium | TC-40 | Pending |
| FR-10 | Secure credential storage in NVS | Security Req | Critical | TC-50 | Pending |

---

# 6. Acceptance Criteria

The device will be considered QA Approved if:

1. 100% of High and Critical priority requirements pass.
2. At least 95% of total test cases pass.
3. No open Critical or High severity bugs remain.
4. Device completes:
   - 72-hour stability test without crash.
   - 7-day endurance test without memory leak.
5. Sensor accuracy within defined tolerances.
6. No data loss in offline/online transition scenarios.
7. Secure credential storage verified.

---

# 7. QA Test Categories

---

## 7.1 Functional Behavior Test

**Objective:**  
Verify that the device features behave as expected according to technical specifications and user requirements.

### Features to be Tested

#### 1. Power & Wake-Up
- Timer wake-up behavior  
- Reed short press (normal cycle)  
- Reed long press (BLE configuration mode)  
- Reset / unknown wake-up  
- Sleep-by-command logic  
- Scheduled restart (1–2 AM)

#### 2. Sensors & Calibration
- Temperature accuracy  
- Humidity accuracy  
- Offset application  
- Measurement stability  

#### 3. Battery & Charging  
(Expected: 2 hours charging / 100 days autonomy)

- Battery ADC measurement  
- Charging state detection  
- Electrical grid detection  
- Low battery handling  
- OTA restrictions when battery is low  

#### 4. Communication (BLE / WiFi / AWS)
- Device scanning & connection  
- Receiving JSON configuration  
- Sending device status to the app  
- Sending device status message to AWS  
- Saving credentials to NVS  
- Connecting to WiFi using BLE credentials  
- Sensor data upload  
- Timeout safety handling  

#### 5. Time & RTC
- RTC sync via WiFi (verification message)  
- RTC sync without WiFi connection (fallback validation)  

#### 6. Storage (NVS)
- Store sensor data offline  
- Retrieve stored data  
- Upload backlog after reconnection  

#### 7. OTA Updates
- OTA execution conditions  
- OTA protection against cancellation via reed interrupt  
- Timeout safety handling  

#### 8. Alarm System
- Temperature upper threshold  
- Temperature lower threshold  
- Humidity upper threshold  
- Humidity lower threshold  

#### 9. LED Behavior
- Reed interaction blink  
- WiFi connection indicator  
- AWS transmit indicator  
- BLE mode indicator  
- Sleep-by-command state indicator  

---

## 7.2 Performance Test

**Objective:**  
Assess responsiveness, stability, and reliability under sustained operation.

### Tests Included

- Medium-run endurance test (72h–7 days)  
- Crash detection  
- Reset detection  
- Memory stability monitoring  
- Reconnection time measurement  

---

## 7.3 Network Test

**Objective:**  
Test device behavior under real and simulated connectivity conditions.

### Tests Included

- Low bandwidth simulation  
- High latency simulation  
- Unstable WiFi conditions  
- Forced WiFi disconnection cycles  
- AWS downtime simulation  
- Data integrity verification after reconnection  

**Best Practice:**  
Use network virtualization tools to mimic real-world instability scenarios and validate recovery logic.

---

## 7.4 Usability Test

**Objective:**  
Ensure the device is easy to use and understandable in real field conditions.

### Tests Included

- Reed magnet usability (press timing clarity)  
- LED clarity and readability  
- RGB error messaging understandability  
- Behavior clarity when:
  - WiFi fails  
  - AWS fails  
  - BLE fails  

---

## 7.5 Sensor Status & Data Validation

**Objective:**  
Verify that sensor and battery data are accurate and correctly transmitted to AWS.

### Tests Included

- Compare temperature with reference sensor  
- Compare humidity with reference sensor  
- Battery measurement vs multimeter  
- Timestamp accuracy validation  
- AWS data integrity check  
- Data consistency across offline/online cycles  

---

## 7.6 Security Test

**Objective:**  
Verify secure handling of credentials, communication, and firmware updates.

### Tests Included

- Secure WiFi credential storage  
- BLE data protection validation  
- AWS authentication integrity  
- Token persistence & expiration handling  
- Protection against invalid JSON injection  
- Secure OTA update validation  

**Reference:**  
ISO standards for safety, quality, and interoperability.


# 8. Test Case Template

Each test case must follow this structure:

## Template

Test Case ID: TC-XX  
Requirement ID: FR-XX  
Title: Short Description  

Preconditions:
- Device powered  
- Firmware v0.1.0 flashed  

Test Steps:
1. Step 1  
2. Step 2  
3. Step 3  

Expected Result:
- Clear measurable outcome  

Actual Result:
- To be filled during execution  

Status:
- Pass / Fail / Blocked  

Severity (if failed):
- Low / Medium / High / Critical  

Tester:
- Name  

Date:
- DD/MM/YYYY  

---

# 9. QA KPIs

| KPI | Target |
|------|--------|
| Requirement Coverage | 100% |
| Test Case Execution Rate | ≥ 95% |
| Critical Bug Leakage | 0 |
| High Severity Open Bugs | 0 before release |
| Reconnection Success Rate | ≥ 98% |
| OTA Success Rate | ≥ 99% |
| Stability (72h) | 0 crashes |
| Data Loss Rate | 0% |

---

# 10. Risk Assessment

| Risk ID | Risk Description | Impact | Probability | Mitigation |
|----------|----------------|---------|------------|------------|
| R-01 | Memory leak during long-run test | High | Medium | 7-day endurance testing |
| R-02 | WiFi instability causing data loss | High | High | Offline storage validation |
| R-03 | Incorrect sensor calibration | Medium | Medium | Reference sensor validation |
| R-04 | OTA failure during low battery | High | Medium | Battery threshold validation |
| R-05 | Credential exposure risk | Critical | Low | Encrypted storage validation |

---

# 11. QA Execution

| Role | Name | Signature | Date |
|------|------|----------|------|
| QA Lead 1 | Daniel Escobar Saltarén | - | - |
| QA Lead 2 | Mateo Robayo | - | - |
| QA Lead 3 | Mauricio Valencia | - | - |
| QA Lead 4 | Cristian Acevedo | - | - |
| Firmware Lead | Isabella García Saenz | - | - |
| Hardware Lead | Ana María Montañez | - | - |

---

# 12. Approval

| Role | Name | Signature | Date |
|------|------|----------|------|
| CEO | Daniel Escobar Saltarén | - | - |
| CTO | Tomas Correa | - | - |

---

# 13. Document Control

| Version | Date | Author | Description |
|----------|--------|---------|-------------|
| 0.1.0 | 16/02/2026 | QA Team | Initial QA Process Definition |

---
