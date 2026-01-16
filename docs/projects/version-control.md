# Version control and collaboration

## Context

This project was developed as a team effort involving multiple technical layers, including industrial connectivity, data pipelines, and XR application development. Effective version control was essential to enable parallel work while avoiding conflicts and unnecessary repository growth.

My contribution included defining and supporting practical version control practices adapted to the specific tools used in the project.

---

## Unity project version control

The Unity application was developed collaboratively and hosted in a shared GitHub repository:

https://github.com/Sallamhamza/unity-hololens-industrial-data

Unity projects generate a large number of files, many of which should not be versioned. Without a disciplined approach, repositories quickly become bloated and difficult to maintain.

To address this, the team followed an established Unity version control workflow, including:

• Use of an appropriate `.gitignore` for Unity projects  
• Versioning only source assets and configuration files  
• Excluding generated, cached, and platform-specific artifacts  

The procedure followed by the team is summarized in the reference material linked below:

• Unity version control procedure (video reference used by the team)  
  https://www.youtube.com/watch?v=dKPdNzETQr8  

This approach enabled parallel development while keeping the repository clean and manageable.

---

## Node-RED version control

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
