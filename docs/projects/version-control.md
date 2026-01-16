# Version control and collaboration

## Context

This project was developed as a team effort involving multiple technical layers, including industrial connectivity, data pipelines, and XR application development. Effective version control was essential to enable parallel work while avoiding conflicts and unnecessary repository growth.

My contribution included defining and supporting practical version control practices adapted to the specific tools used in the project.

---

## Project repository structure and workflow

The project was developed using a single shared GitHub repository that served as the main integration point for all system components, including XR application code, data pipeline logic, and supporting configuration.

https://github.com/Sallamhamza/unity-hololens-industrial-data

Work was organized using a feature-based branching strategy, where each team member was responsible for implementing and maintaining a specific feature or subsystem in a dedicated branch. This approach allowed parallel development while preserving a clear integration path into the main branch.

My individual contributions are traceable in the following branch:

https://github.com/Sallamhamza/unity-hololens-industrial-data/tree/feature/p1-data

This branch contains the Node-RED integration work, REST API logic, and supporting configuration corresponding to my assigned feature scope.

---

## Specifics about Node-RED version control

By default, Node-RED does not provide built-in support for version control of flows. To address this limitation, **Node-RED Projects mode** was enabled.

Projects mode allows Node-RED flows to be:

• Stored as structured files  
• Tracked using Git  
• Versioned and reviewed like conventional source code  

The official Node-RED documentation used as reference is linked below:

• Node-RED Projects documentation  
  https://nodered.org/docs/user-guide/projects/  

Enabling Projects mode was a key step to treat Node-RED flows as maintainable engineering artifacts rather than ad-hoc configurations.

---

## Unity-specific version control considerations

The Unity user interface and XR interaction cleanup were developed by another team member in a separate feature branch:

https://github.com/Sallamhamza/unity-hololens-industrial-data/tree/feature/p3-ui-clean

The Unity component required additional version control considerations due to the large number of generated and platform-specific files produced by Unity.

To address this, the team followed an established Unity version control workflow, including:

• Use of an appropriate `.gitignore` for Unity projects  
• Versioning only source assets and configuration files  
• Excluding generated, cached, and platform-specific artifacts  

This procedure is summarized in the reference material linked below:

• Unity version control procedure (video reference used by the team)  
  https://www.youtube.com/watch?v=dKPdNzETQr8  

This ensured that Unity development could proceed in parallel without degrading repository quality.


---

## Supporting documentation

In addition to the public documentation above, internal project documentation was used to coordinate collaboration and clarify responsibilities across the team.

Relevant reference documents include:

• Individual Project Portfolio (academic submission)  
• Manufacturer documentation for PLC connectivity and APIs  

These documents provided traceability between design decisions, implementation choices, and final outcomes.

---

## Collaboration practices

Version control practices were aligned with the collaborative nature of the project:

• Clear separation of responsibilities across system layers  
• Regular synchronization of changes through GitHub  
• Shared understanding of which components were owned individually versus collaboratively  

These practices reduced integration friction and supported steady progress across sprints.

---

## Outcome

The adopted version control approach enabled:

• Parallel development across Unity and data pipeline layers  
• Reduced risk of accidental overwrites or data loss  
• Clear traceability of changes in both code and configuration  
• A repository structure suitable for future extension and maintenance  

This experience reinforced the importance of adapting version control strategies to the specific characteristics of each tool in the technology stack.
