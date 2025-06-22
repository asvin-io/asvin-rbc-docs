======================
Risk by Context™ Model
======================
The Risk-by-Context™ architecture is a modular, data-driven system purpose-built to support advanced OT risk management through real-time contextual analysis. It comprises a layered architecture that includes a web-based frontend for interactive risk visualization, a scalable backend API layer for orchestrating services, a graph-based data store for managing cyber risk relationships, and a powerful analytics engine for computing the dynamic RBC-Index. The system leverages modern microservices principles to ensure scalability, maintainability, and loose coupling between components. Central to its design is the cyber risk knowledge graph, which integrates diverse contextual signals—such as business impact, network segmentation, and operational dependencies—allowing the analytics engine to continuously recalculate risk scores based on live data. This architecture enables seamless integration with external data sources (e.g., asset inventories, vulnerability feeds, BCP systems), supports real-time notifications, and offers RESTful APIs for downstream systems.

    .. image:: ../images/rbc-arch.png
        :alt: Risk by Context™ architecture
        :width: 800pt
        :align: center

Risk by Context™ Portal
-------------------------

The Risk by Context™ Portal, developed using TypeScript and the Angular framework, provides a powerful and intuitive interface for monitoring and managing OT cybersecurity risks. Designed to handle the complexities of industrial environments, it offers an interactive dashboard that presents a real-time risk posture of the entire OT infrastructure. Security teams can drill down into network segments and individual OT devices, gaining granular insights into their risk exposure vulnerabilities, and threat associations.

One of Risk by Context™ key strengths is its graph-based visualization engine, which dynamically maps the relationships between assets, threats, and vulnerabilities. This capability reveals the hidden interdependencies within the OT network, exposing potential attack paths and systemic risks that traditional list-based approaches fail to capture. By leveraging advanced risk modeling, the system provides context-aware risk prioritization at three critical levels: location, network segment, and device.

The platform also integrates real-time threat intelligence and historical risk trends, enabling security teams to make informed, data-driven decisions. Through an adaptive and visually driven approach, Risk by Context™ transforms complex OT risk landscapes into actionable insights, empowering organizations to enhance cyber resilience, reduce downtime, and protect critical operations effectively.

Risk by Context™ Engine
-------------------------

The Risk by Context™ Engine, built in C# using the .NET framework, is a high-performance, microservices-based system designed for scalable and efficient OT risk management. It provides a comprehensive set of REST APIs that collect contextual data from the OT environment, including locations, network segments, and devices. This data is then processed to construct a cybersecurity knowledge graph, mapping the relationships between assets, threats, and vulnerabilities to provide a context-aware risk assessment.

At the core of the system is the RBC-Index, a dynamic, multi-dimensional risk score that continuously evaluates cybersecurity risks at location, segment, and device levels. By leveraging real-time and historical data, the Engine ensures adaptive risk prioritization, helping organizations focus on the most critical threats. Additionally, it offers customized risk reports via dedicated APIs, tailored for different roles, including C-level executives, managers, security engineers, and risk analysts.

Designed with a microservices architecture, the Engine ensures high availability, scalability, and fault tolerance, allowing seamless integration with threat intelligence feeds, SIEM platforms and asset management systems. All REST APIs are secured using JWT-based access tokens, ensuring strong authentication and authorization. With its efficient data processing and real-time risk analysis capabilities, the Risk by Context™ Engine empowers organizations to proactively mitigate OT security risks, strengthen cyber resilience, and enhance operational security without compromising performance.

Context Database
----------------
The Context Database architecture is designed to efficiently manage large-scale, context-rich OT data,leveraging a hybrid approach with MongoDB (NoSQL) and Neo4j (graph database) to support the Engine’s microservices framework. Both databases run in Docker containers, ensuring high availability, scalability, and fault tolerance while seamlessly integrating with the risk analysis Engine.

MongoDB serves as the primary storage for unstructured contextual data, capturing critical details about locations, network segments, and OT devices. The Engine processes and structures this raw data, transforming it into a cybersecurity knowledge graph stored in Neo4j. This graph-based model enables deep relationship mapping, allowing security teams to visualize complex interdependencies, attack pathways, and systemic vulnerabilities across the OT environment.

By combining the flexibility of NoSQL with the analytical power of graph databases, Risk by Context™ ensures fast query performance, real-time risk analysis, and dynamic threat prioritization. This context-aware, scalable data architecture enables security teams to gain deep, actionable insights, strengthening proactive defense strategies, and enhancing overall OT cyber resilience.


