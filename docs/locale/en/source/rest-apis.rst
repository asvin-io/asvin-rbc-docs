REST API
========

Introduction
------------

The Risk by Context™ platform provides a robust and extensible set of RESTful APIs designed to support seamless integration with external systems and applications. These APIs enable programmatic access to all major components and functionalities of the RBC system, allowing for both automation and interoperability across diverse environments.

The API suite covers a broad range of management operations, including:

- **Location and Segment Management**: Define and organize network topologies and operational zones.
- **Device Management**: Register, update, and monitor connected devices within the infrastructure.
- **Vulnerability Management**: Ingest and track vulnerability data for proactive risk evaluation.
- **User and Access Management**: Control user roles, permissions, and authentication.
- **Interface Management**: Configure external data sources or destinations for context and insight exchange.
- **Report Management**: Generate, retrieve, and archive risk-related reports.
- **Risk Insights**: Access computed risk scores and contextual intelligence for informed decision-making.

Each API follows RESTful design principles, utilizing standard HTTP methods (GET, POST, PUT, DELETE) and supports secure communication through token-based authentication.

These APIs are ideal for organizations looking to integrate RBC capabilities with existing workflows, such as:

- Pulling real-time risk scores into SIEM or SoC platforms.
- Automating device vulnerability ingestion.
- Synchronizing configuration data across distributed systems.

This chapter provides detailed documentation for each API endpoint, including request parameters, response formats, authentication methods, and usage examples. It is intended for developers, system integrators, and DevOps teams working to embed RBC functionalities into their operational infrastructure.

API Endpoints
-------------

.. openapi:: ./_static/code/swagger.json



