# XR industrial data pipeline

## Context

This section demonstrates an end-to-end industrial data pipeline where live signals from Siemens PLCs are acquired, processed, and visualized in an extended reality application running on Microsoft HoloLens 2.

The work was developed as a team project. This page focuses on my individual contributions to the system design, data pipeline, and integration layers.

## System overview

At a high level, the system consists of:

• Siemens PLCs providing operational and inventory signals  
• OPC UA as the primary industrial communication protocol  
• Node-RED as an intermediate processing and API layer  
• Unity as the application logic layer  
• Microsoft HoloLens 2 as the visualization device  

The pipeline enables real-time visualization of station state, hopper levels, alarms, and feeder information.

## My responsibilities

My main responsibilities in this User Story were:

• Level 1 connectivity and validation  
• OPC UA signal discovery and testing  
• Node-RED flow design and implementation  
• REST API design for Unity consumption  
• Data aggregation into station-level JSON objects  
• Support during XR deployment and testing  

## End-to-end data flow

The final pipeline enables Unity to retrieve all relevant information for a station using a single API call.

This design decision reduced coupling between the XR application and the underlying PLC structure, and simplified future extension to additional stations.

The final results of this pipeline are visible in:

• Figure 13 – Unity panel showing simulated data  
• Figure 14 – Node-RED flow serving real PLC data  
• Figure 17 – Unity application displaying live SIF402 data  
• Figure 22 – HoloLens visualization of feeder counts  
• Figure 24 – Simultaneous visualization of SIF402 and SIF405  

## Outcome

The implemented solution successfully demonstrated:

• Stable PLC communication  
• Clear separation between industrial and application layers  
• Real-time XR visualization of industrial data  
• A reusable architecture for additional stations  

This pipeline formed the technical backbone of the XR application.
