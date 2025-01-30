---
{"dg-publish":true,"permalink":"/software/mermaid-diagrams/basic-mermaid-syntax/","tags":["Mermaid","script","charts"]}
---

## Mermaid syntax

Diagrams are created by linking text labels using arrow connectors. You can choose different shapes, add labels to connectors, and style connectors and shapes.

[Mermaid documentation for the complete syntax and styling options](https://mermaid.js.org/intro/syntax-reference.html)

|                      |                                                  |                                |
| -------------------- | ------------------------------------------------ | ------------------------------ |
| **Shape styles**     | `[rectangle]`                                    | `(rounded rectangle)`          |
|                      | `((circle))`                                     | `{diamond}`                    |
| **Connector styles** | arrow: `A-->B`                                   | dotted: `A-.-->B`              |
|                      | no arrow: `A---B`                                | with a label: `A-->\|label\|B` |
| **Diagram types**    | `graph`                                          | `pie`                          |
|                      | `gantt`                                          | `sequenceDiagram`              |
|                      | `stateDiagram`                                   | `classDiagram`                 |
|                      | `gitgraph`                                       | `flowchart`                    |
|                      | `mindmap`                                        | `requirementDiagram`           |
|                      | `erDiagram`                                      | `journey`                      |
|                      | `C4Context`                                      |                                |
| **Gantt**            | task state: `done`, `active`, `crit`, `after`    | `section`                      |
| **Pie**              | `title`                                          |                                |
| **Gitgraph**         | actions: `commit`, `branch`, `checkout`, `merge` |                                |
| **UML**              | lifelines:`participant`                          | `activate`                     |
|                      | containers: `loop`, `alt`, `opt`                 | `class`                        |
| **Information**      | comment: `%%`                                    | `note`                         |

The full syntax reference is [here:]([Diagram Syntax | Mermaid](https://mermaid.js.org/intro/syntax-reference.html))