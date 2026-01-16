# Unity and HoloLens integration

## Role and scope

While the Unity application and XR interaction logic were developed collaboratively, my role focused on ensuring that industrial data could be reliably consumed by Unity through well-defined APIs.

This page documents the integration perspective.

## API consumption in Unity

Unity scripts were implemented to fetch data from the Node-RED REST endpoints and deserialize the returned JSON into application data structures.

An example of the C# code used to fetch and parse station data is shown in:

• Figure 12 – C# script for API data retrieval  

## Simulation strategy

To enable development without continuous access to the PLC network, simulated OPC UA signals were introduced.

This allowed:

• Independent development of Unity logic  
• Verification of API structure  
• Testing of XR visualization behavior  

Simulation elements are illustrated in:

• Figure 10 – Simulated OPC UA signals  
• Figure 11 – Node-RED flow providing simulated data  

## Verification of live data

Once connectivity was established, simulated signals were replaced with real PLC data.

The successful transition is demonstrated in:

• Figure 13 – Unity panel with simulated data  
• Figure 17 – Unity panel with live PLC data  

## Deployment support for HoloLens 2

I participated in testing, debugging, and deployment activities for the HoloLens application.

This included:

• Verifying network accessibility of Node-RED APIs  
• Assisting with deployment troubleshooting  
• Validating live data visualization on device  

Final XR results are shown in:

• Figure 22 – HoloLens visualization of feeder data  
• Figure 24 – Simultaneous station visualization  

![Live data demo](../assets/gifs/DemoStations2and5.gif)

## Outcome

The integration confirmed that:

• The REST APIs were stable and fit for XR consumption  
• The data model supported both simulation and live operation  
• The system could be deployed and tested on HoloLens 2  

This validated the overall architecture from industrial signal to XR visualization.



