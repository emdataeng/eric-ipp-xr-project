# Node-RED and OPC UA integration

## Scope of contribution

This page documents my primary technical contribution to the User Story: establishing reliable industrial connectivity and transforming raw PLC signals into structured REST APIs consumable by Unity.

## OPC UA connectivity and validation

Before implementing any Node-RED logic, PLC communication was validated using an OPC UA browser.

Key steps included:

• Identifying PLC IP addresses from manufacturer documentation  
• Inspecting available variables and browse paths  
• Verifying data types and update behavior  

This process is illustrated in:

• Figure 4 – OPC UA browser view for station SIF402  
• Figure 19 – OPC UA browser view for station SIF405  

## Node-RED environment setup

Node-RED was installed on Windows and tested in both native and containerized environments.

The initial setup with OPC UA nodes installed is shown in:

• Figure 1 – Node-RED with OPC UA nodes available  

Early testing highlighted networking challenges when using Docker with WSL2, particularly regarding OPC UA discovery.

## Reading PLC data via OPC UA

PLC data was accessed using Node-RED OPC UA client nodes.

Initial tests focused on single variables and were later extended to multiple signals per station.

Examples include:

• Figure 6 – Reading a single PLC signal via OPC UA  
• Figure 7 – Scaling to multiple PLC signals  

## REST API design in Node-RED

To expose PLC data to Unity, REST endpoints were implemented using Node-RED HTTP In and HTTP Out nodes.

Key design aspects:

• Retaining the latest signal snapshot using flow context  
• Returning structured JSON responses  
• Handling unavailable data gracefully  

This is illustrated in:

• Figure 8 – REST endpoint implementation  
• Figure 9 – Example API response  

## Data aggregation per station

During later sprints, multiple signals were aggregated into single station-level JSON objects to minimize API calls from Unity.

For station SIF402, this included:

• Running time  
• Electrical current  
• Alarm state  
• Hopper presence and minimum level  

The aggregation logic and resulting API are shown in:

• Figure 15 – Aggregated Node-RED flow for SIF402  
• Figure 16 – API response for SIF402  

A similar approach was applied to station SIF405:

• Figure 20 – Node-RED flow for SIF405 feeders  
• Figure 21 – API response for SIF405  

## Reuse and scalability

Operational data flows were reused across stations by changing only PLC endpoints, as shown in:

• Figure 23 – Reused operational data flow for SIF405  

This validated the scalability of the Node-RED based architecture.
