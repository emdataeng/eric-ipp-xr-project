# Node RED and OPC UA integration

## Scope of contribution

This page documents my primary technical contribution to the project: establishing reliable industrial connectivity and transforming raw PLC signals into structured REST APIs consumable by Unity.

My responsibilities covered signal discovery, Node RED flow design, REST API implementation, and station level data aggregation for SIF 402 and SIF 405.

## Connectivity validation using the SIF API

Before implementing OPC UA flows in Node RED, connectivity to the SIF system was validated using the SIF API checker endpoint. This provided a fast confirmation that the system was reachable and operational.

![Figure 2 – API checker response](../assets/images/node-red-opcua/fig02-api-checker-response.png)

Figure 2 – Response obtained from the GET request to the checker endpoint. Success true confirms that the API is working

## Node RED environment setup

Node RED was installed and configured with OPC UA client nodes to enable communication with Siemens PLCs.

![Figure 1 – Node RED with OPC UA nodes installed](../assets/images/node-red-opcua/fig01-node-red-opcua-setup.png)

Figure 1 – Initial Node RED setup showing OPC UA nodes available

This setup was tested both on Windows and in containerized environments. Early tests highlighted networking considerations when using Docker with WSL2, particularly for OPC UA communication.

## OPC UA signal discovery

Before implementing Node RED flows, PLC communication was validated using an OPC UA browser to inspect available signals, browse paths, and data types.

SIF 402 discovery example:

![Figure 4 – OPC UA browser for station SIF 402](../assets/images/node-red-opcua/fig04-opcua-browser-sif402.png)

Figure 4 – OPC UA browser view showing available signals for station SIF 402

SIF 405 discovery example:

![Figure 19 – OPC UA browser for station SIF 405](../assets/images/node-red-opcua/fig19-opcua-browser-sif405.png)

Figure 19 – OPC UA browser view showing feeder related signals for station SIF 405

## Reading PLC data via OPC UA in Node RED

Initial Node RED flows focused on reading a single PLC signal to validate connectivity and data integrity.

![Figure 6 – Reading a single PLC signal via OPC UA](../assets/images/node-red-opcua/fig06-opcua-single-signal.png)

Figure 6 – Node RED flow reading a single PLC signal through OPC UA

Once validated, the flow was extended to read multiple signals in parallel.

![Figure 7 – Reading multiple PLC signals via OPC UA](../assets/images/node-red-opcua/fig07-opcua-multiple-signals.png)

Figure 7 – Node RED flow scaled to read multiple PLC signals

## REST API implementation

To expose PLC data to the Unity application, REST endpoints were implemented using Node RED HTTP In and HTTP Out nodes.

![Figure 8 – REST API endpoint implementation in Node RED](../assets/images/node-red-opcua/fig08-node-red-rest-endpoint.png)

Figure 8 – Implementation of a REST API endpoint returning the latest PLC data

Flow context was used to retain the latest snapshot of each signal, ensuring that API calls returned a consistent state.

## Station level data aggregation for SIF 402

Multiple SIF 402 signals were aggregated into a single JSON object to minimize API calls from Unity. The packed payload included operational signals and hopper state.

![Figure 15 – Aggregated Node RED flow for SIF 402](../assets/images/node-red-opcua/fig15-sif402-aggregated-flow.png)

Figure 15 – Node RED flow aggregating operational and hopper data for station SIF 402

The resulting API response exposed all relevant station data in a single request.

![Figure 16 – Aggregated API response for SIF 402](../assets/images/node-red-opcua/fig16-sif402-api-response.png)

Figure 16 – REST API response containing aggregated station data for SIF 402

## Data identification and extraction for SIF 405 feeders

For SIF 405, the first step was to identify variables related to the number and type of caps in each feeder by filtering the available signals list.

![Figure 18 – Filtered variable list for SIF 405](../assets/images/node-red-opcua/fig18-sif405-variable-list.png)

Figure 18 – List of variables filtered for station SIF 405

A Node RED flow was then implemented to read these signals via OPC UA and expose them through a REST endpoint, while also including a simulation path for development and testing.

![Figure 20 – Node RED flow for SIF 405 feeders](../assets/images/node-red-opcua/fig20-sif405-feeders-flow.png)

Figure 20 – Node RED flow to extract SIF 405 feeder data. The upper section reads PLC data and the lower section supports simulation

The resulting feeder endpoint response is shown here:

![Figure 21 – API response for SIF 405 feeders](../assets/images/node-red-opcua/fig21-sif405-feeders-api-response.png)

Figure 21 – REST API response for SIF 405 feeders data

## Reuse of operational signals for SIF 405

The operational signals already implemented for SIF 402, running time, current, and alarm state, were replicated for SIF 405 by reusing the same logic and changing the PLC endpoint, while removing hopper specific signals.

![Figure 23 – Operational data flow for SIF 405](../assets/images/node-red-opcua/fig23-sif405-operational-flow.png)

Figure 23 – Node RED flow implemented to get operational data from SIF 405 using the same structure as for SIF 402

## Outcome

The Node RED and OPC UA layer achieved:

• Stable PLC communication for SIF 402 and SIF 405  
• Clear separation between industrial and application layers  
• Station level data aggregation to reduce Unity API calls  
• REST APIs suitable for XR consumption  
• Reusable flow patterns across stations
