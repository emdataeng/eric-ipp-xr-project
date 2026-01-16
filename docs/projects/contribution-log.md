# Individual contribution log

This page documents my individual contribution to the project in a chronological manner, following the sprint structure, user stories, and tasks defined during the project. The content is derived from the sprint-based organization used in the IPP2 submission.

The purpose of this log is to make my work traceable, concrete, and verifiable.

---

## Sprint 1

### User Story 1 – PLC and Node-RED setup

**Description**  
As a PLC/OPC developer, I want to connect Siemens PLCs to Node-RED via OPC UA so that machine data becomes available for streaming.

---

### Task 1 – Installing Node-RED and implementing OPC UA nodes

**Description**  
After reading the Node-RED general guide and the Windows installation guide, Node-RED was installed on Windows 11 and additional OPC-related nodes were installed as well.

At first, a containerized infrastructure was conceived in which Node-RED and later InfluxDB would be deployed in Docker containers. To this end, Node-RED was also installed on a Linux-based container following the provided instructions.

**Challenge**  
When using containers, it is advisable to understand how networking is implemented in Docker, especially when using WSL2 on Windows 11 as the host system. Otherwise, the Node-RED instance is not able to “see” the OPC UA simulator or the actual PLC.

Regardless of the platform, the outcome is a Node-RED instance running and accessible through  
http://127.0.0.1:1880/

---

### Tasks 2 and 3 – Connecting to PLC Siemens in stations SIF-402 and SIF-405

**Description**  
Data access to the Siemens PLC controlling station SIF-402 was validated using two approaches: the SIF API and direct OPC UA communication. The API was first tested to quickly confirm connectivity and available endpoints by consulting the manufacturer documentation. Initial tests using the checker and inventory endpoints confirmed correct operation and returned station-level inventory data. In parallel, OPC UA communication was validated using an [OPC UA browser](https://prosysopc.com/products/opc-ua-browser/) to understand the PLC address space and verify signal availability before integration with Node-RED.

**Challenge**  
Navigating the OPC UA object tree was initially non-intuitive, and relevant signals were not immediately obvious. Understanding the PLC address structure required careful inspection of the object hierarchy and cross-referencing manufacturer documentation and signal lists.

---

### Task 4 – Connecting to PLC Siemens in station SIF-405 via OPC UA in node-red

**Description**  
To access the PLC data available trough the OPC UA server running on each PLC, we must use the OPC UA client node in node-red, in this case the “RunningTime” signal was selected arbitrarily to run this test, and all the metadata required was extracted from the OPC UA browser.

**Challenge**  
Using node-red for the first time might be overwhelming, therefore I advise checking these videos from [node-red academy](https://node-red-academy.learnworlds.com/path-player?courseid=node-red-getting-started&unit=6790b6c583e32519770d179cUnit) which are perfect for understanding the basics as well as the intermediate features.

Coding in node-red is done in JavaScript, in principle is not required to know the language, especially if using assistance from generative AI agents, however understanding programming logic is definitively a skill that comes handy here to process and transform the raw signals into a structured format that can later be processed by the Unity application.


---

## Sprint 2

### User Story – Accessing PLC data through OPC UA

**Description**  
As a PLC/OPC developer, I want to access PLC data through OPC UA so that real-time values can be retrieved and processed.

---

### Task – Connecting Node-RED to the OPC UA simulator

**Description**  
OPC UA client nodes were configured in Node-RED to connect to the [OPC UA simulator](https://prosysopc.com/products/opc-ua-simulation-server/). Relevant variables were selected and tested to confirm correct data acquisition.

**Challenge**  
Browsing large OPC UA address spaces and identifying relevant variables required careful inspection and validation.

---

## Sprint 3

### User Story – Exposing PLC data to external applications

**Description**  
As an application developer, I want to expose PLC data through an API so that it can be consumed by external applications such as Unity.

---

### Task – Creating REST endpoints in Node-RED

**Description**  
HTTP endpoints were created in Node-RED to expose PLC data in JSON format. These endpoints were tested locally to verify correct responses.

**Challenge**  
Exposing raw PLC variables resulted in multiple API calls and increased complexity on the client side.

---

## Sprints 4 and 5

### User Story – Reformat data from SIF402

**Description**  
The previous sprint served as a test for extracting, processing, and displaying data from SIF402. However, after running tests in Unity, it was concluded that the data needed to be reformatted to allow retrieval through a single API call.

---

### Task – Reformat data from SIF402

**Description**  
The Node-RED logic was updated to aggregate multiple variables from SIF402 into a single structured JSON object representing the station state.

**Challenge**  
Ensuring that all values were coherent at the time of the API response required careful handling of data updates.

---

### User Story – Support XR integration and deployment

**Description**  
As a project team member, I want to support XR integration and deployment so that the application can be validated on HoloLens 2.

---

### Task – Integration testing and deployment support

**Description**  
Integration testing was performed between Node-RED and the Unity application. Deployment and runtime behavior were tested on Microsoft HoloLens 2.

**Challenge**  
Network configuration and connectivity between the XR device and backend services required additional validation and troubleshooting.
