========================
Install Risk by Context™
========================
This section provides instructions for installing Risk by Context™ using pre-built Docker images and from source.

Using Pre-built Docker images
-----------------------------
asvin provides docker images for Risk by Context™ to run in containers. It is the fastest way to setup the solution.

Prerequisites
^^^^^^^^^^^^^
- Install `Docker <https://docs.docker.com/engine/install/>`_
- Install `Docker compose <https://docs.docker.com/compose/>`_
- Operating system Ubuntu, Mac or Windows with WS2

Create and Start Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. _start-using-docker:

using docker CLI
"""""""""""""""""
Use standard `docker` commands if you prefer working directly with containers.

.. code-block:: sh

   docker run --name asvin-rbc-portal -p 8080:80  -d asvin-rbc-portal:<tag>
   docker run --name asvin-rbc-device-service -p 5001:5001 -d asvin-rbc-device-service:<tag>
   docker run --name asvin-rbc-report-service -p 5002:5002 -d asvin-rbc-report-service:<tag>
   docker run --name asvin-rbc-mongo -p 27017:27017 -v $PWD/rbc-data/context:/data/db -d mongo:<tag>
   docker run --name asvin-rbc-neo4j -p 7474:7474 -p 7687:7687 -v $PWD/rbc-data/graph:/data -d neo4j:<tag>

.. _start-using-docker-compose:

using docker compose
"""""""""""""""""""""
Docker Compose offers a simpler way to start all containers simultaneously. All Risk by Context™ components are configured in the docker-compose.yml file, which also defines the port mappings and volume configurations for each service.

  1. Download the :download:`docker-compose.yml <../_static/code/docker-compose.yml>` file
  
  2. Start the containers with :code:`docker compose up -d`

using RBC CLI
"""""""""""""
Start all containers with a :term:`RBC CLI` command.

.. code::

   /.rbc up

Access the Portal
^^^^^^^^^^^^^^^^^
Once the Portal container is running, you can access it at `<http://localhost:8080>`_.

Building from source
--------------------
You can clone the Git repositories and build the Risk by Context™ components from source manually.

Prerequisites
^^^^^^^^^^^^^
- `Git <https://git-scm.com/downloads>`_
- `Node.js <https://git-scm.com/downloads>`_
- `.NET SDK and .NET Runtime <https://learn.microsoft.com/en-us/dotnet/core/install/>`_

Build and Run
^^^^^^^^^^^^^
- Risk by Context™ Portal

.. code-block:: bash

   git clone <rbc-portal-git-repo>
   npm install
   npm start

- Risk by Context™ Engine

.. code-block:: bash

   git clone <rbc-engine-git-repo>
   dotnet build
   dotnet run

- Then access the Portal at `<http://localhost:8080>`_.
