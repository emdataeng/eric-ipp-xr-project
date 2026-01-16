# Benefits, limitations, system requirements and ethics

## Potential benefits

• Enables real-time visualization of industrial process data in XR  
• Improves situational awareness for operators and trainees  
• Decouples industrial systems from XR applications through stable APIs  
• Supports simulation-first development, reducing dependency on live equipment  

## Limitations

• System depends on stable network connectivity between PLCs, backend services, and XR devices  
• OPC UA address spaces can be complex and vendor-specific  
• XR hardware availability and setup introduce deployment overhead  
• The solution is a prototype and not production-hardened  

## System requirements

### Software
• Siemens PLCs with OPC UA support  
• Node-RED with OPC UA and HTTP nodes  
• Unity with MRTK (UWP build support)  
• Visual Studio 2022 with ARM64 and UWP components  

### Hardware
• Industrial PLC hardware  
• Development PC running Windows  
• Microsoft HoloLens 2  

### Integration
• Network access between development computers, PLCs, Node-RED and XR devices  
• Firewall configuration allowing REST API communication  

## Ethical considerations

This project involves the visualization of industrial process data and interaction with operational systems.

Key ethical considerations include:

• **Data privacy**: Only non-personal, operational machine data was used  
• **User safety**: XR visualization must not distract operators during critical operations  
• **System reliability**: Incorrect or delayed data visualization could lead to unsafe decisions  
• **Responsibility and accountability**: XR systems should support, not replace, human judgment  

## Stakeholder matrix

| Stakeholder | Interest | Responsibility | Ethical concern |
|------------|---------|----------------|----------------|
| Operators | Use XR for awareness | Correct interpretation | Safety, distraction |
| Engineers | System maintenance | Data accuracy | Reliability |
| Management | Decision support | Oversight | Misuse of data |
| Organization | Deployment | Governance | Compliance |
