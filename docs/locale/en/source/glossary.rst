=========
Glossary
=========

Risk by Context™ provides a glossary to ensure a clear and consistent understanding of key cybersecurity and OT-related terms. It helps users interpret contextual parameters, risk assessment factors, and security controls accurately. A well-defined glossary enhances communication, reduces ambiguity, and supports effective decision-making within the Risk by Context™ system.

.. glossary::

    Context
      Context refers to the circumstances, environment, and additional information surrounding an OT device, which help assess its operational state, security posture, and potential risks.

    Contextual Data
      Contextual data refers to information that enhances risk assessment by incorporating relevant environmental and situational factors. In RBC, contextual data includes elements such as network segment size, operational significance, and business continuity plans helping to understand context of devices in a OT environment to assess and prioritize their cyber security risks.

    Docker Container
      A runtime instance of a Docker image. Managed in the :term:`RBC CLI` using `start`, `stop`, and `restart` commands.

    Docker Image
      A lightweight, standalone, and executable package that includes everything needed to run a piece of software. Used in the :term:`RBC CLI` via the `load` command.

    Device Service
      The backend mirco-servic written in .NET framework responsible for locations, segments and devices in the RBC ecosystem.

    MongoDB
      A NoSQL database used by the RBC platform to store and retrieve data. Runs in a container and is managed via the utility.

    RBC Portal
      A web-based application that provides a comprehensive view of the OT environment's risk posture. It visualizes real-time risk scores, highlights critical vulnerabilities, and presents contextual insights derived from the RBC-Index, enabling security teams to monitor, assess, and prioritize cyber risks across operational technology assets.

    RBC CLI
      A custom Bash-based command-line tool to manage Docker images and containers for the RBC platform, including services like Portal, Device, and MongoDB. You can download the utility from :download:`here <_static/code/rbc>`. For usage instructions, refer to the :doc:`RBC CLI Reference <getting-started/rbc-cli>`.

    Terminal
      An application that provides a command-line interface (CLI), allowing users to interact with the operating system by entering and executing text-based commands.
    
    

    

    