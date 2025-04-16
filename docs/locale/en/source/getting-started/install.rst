========================
Install Risk by Context™
========================
This guide provides instructions for installing Risk by Context™ using Docker and from source.

Run from Docker images
----------------------
asvin provides docker images for Risk by Context™ to run in containers.

Prerequisites
^^^^^^^^^^^^^
- `Docker <https://docs.docker.com/engine/install/>`_
- Ubuntu or Windows with WS2

Run docker images
^^^^^^^^^^^^^^^^^^
.. _start-using-docker:

1. using docker

.. code-block:: sh

  docker run --name asvin-rbc-portal -p 8080:80  -d asvin-rbc-portal:<tag>
  docker run --name asvin-rbc-device-service -p 5001:5001 -d asvin-rbc-device-service:<tag>
  docker run --name asvin-rbc-report-service -p 5002:5002 -d asvin-rbc-report-service:<tag>
  docker run --name asvin-rbc-mongo -p 27017:27017 -v $PWD/rbc-data/context:/data/db -d mongo:<tag>
  docker run --name asvin-rbc-neo4j -p 7474:7474 -p 7687:7687 -v $PWD/rbc-data/graph:/data -d neo4j:<tag>

.. _start-using-docker-compose:

2. using docker composer

  * copy the `docker-compose.yaml` file
  
    .. literalinclude:: ../snippet/asvin-rbc-docker-compose.yaml
       :language: yaml
       :linenos:
  * Start the containers with :code:`docker compose up -d`

Build from source
-----------------
You can clone the Git repository and build the Risk by Context™ components from source.

Prerequisites
^^^^^^^^^^^^^
- `Git <https://git-scm.com/downloads>`_
- `Node.js <https://git-scm.com/downloads>`_
- `.NET SDK and .NET Runtime <https://learn.microsoft.com/en-us/dotnet/core/install/>`_

Run binary
^^^^^^^^^^
- Risk by Context™ Portal

.. code-block:: bash

   git clone <rbc-portal-git-repo>
   npm i install
   npm start

- Risk by Context™ Engine

.. code-block:: bash

   git clone <rbc-engine-git-repo>
   dotnet build
   dotnet run
  
