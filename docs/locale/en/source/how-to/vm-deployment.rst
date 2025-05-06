============================================
On-premise Deployment using Preconfigured VM
============================================
asvin provides a preconfigured virtual machine (OVA file) that includes all the necessary components and software for Risk by Context™. This method is ideal for users who want to get started quickly without manual installation of dependencies.

Prerequisites
-------------

Before proceeding with the setup, ensure the following requirements are met:

Hardware Requirements
---------------------
  * A 64-bit x86/AMD64 CPU with virtualization support (Intel VT-x or AMD-V).

  * Minimum 2 GB RAM (4 GB or more recommended).

  * Minimum 50 GB free disk space.

  * 1.3GHz or faster core speed

Operating System
^^^^^^^^^^^^^^^^
  * Compatible with Windows 10/11, macOS, or a recent Linux distribution.

VMware Workstation / VMware Player
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  * Install VMware Workstation (Windows/Linux) or VMware Fusion (macOS).

  * Ensure that your VMware product supports running .ova or .vmx files.

Operating System
^^^^^^^^^^^^^^^^
  * Compatible with Windows 10/11, macOS, or a recent Linux distribution.

Virtualization Support
^^^^^^^^^^^^^^^^^^^^^^^
  * Make sure virtualization is enabled in BIOS/UEFI.

Administrative Access
^^^^^^^^^^^^^^^^^^^^^^
  * You must have administrator privileges to install and run VMware and configure network interfaces if needed.

VMware Workstation / VMware Player
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  * Install VMware Workstation or Fusion.

  * Ensure that your VMware product supports running .ova  files.

Download Files
^^^^^^^^^^^^^^^
Ensure you have access to the following files

    * virtual machine image (.ova)

    * docker images

        * Portal:  asvin-rbc-portal.tar

        * Backend: asvin-rbc-device-service.tar

        * Database: asvin-rbc-mongo.tar

    * docker-compose.yml file

🛠️ Setup Guide: Importing the OVA File into VMware
---------------------------------------------------

  Follow the steps below to import the provided .ova file into your VMware application.

.. note::
  Please install all the required tools and download images as described in Prerequisite setup.


Launch VMware
^^^^^^^^^^^^^
Open the VMware application:

  * On Windows/Linux: Open VMware Workstation or VMware Player.
  * On macOS: Open VMware Fusion.
 
Import the OVA File
^^^^^^^^^^^^^^^^^^^^
#. From the main menu, select File → Open.

#. Browse to the location of the .ova file provided (e.g., asvin-rbc.ova).

#. Select the .ova file and click Open.

#. VMware will display an Import Virtual Machine window.

#. Choose a name and destination folder for the virtual machine.

#. Click Import to begin the process.

.. note::
  💡 This may take a few minutes depending on the size of the OVA and the performance of your system.

Power On the VM
^^^^^^^^^^^^^^^^^^^^
Once the import completes:

  * The VM will appear in your VM library.

  * Select the virtual machine and click Power on this virtual machine.

Login Information
^^^^^^^^^^^^^^^^^^^^
Please refer to the specific documentation or accompanying README.md if different credentials or setup scripts are provided.


Post-Setup Verification
------------------------

The virtual machine provided in the .ova file comes with the following software pre-installed and pre-configured:

✅ Docker & Docker Compose
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

  * Docker is installed to support containerized applications.

  * Docker Compose is available to orchestrate multi-container services.

.. note::
  Installed version of docker is 28.1.1 and docker compose v2.35.1

You can verify the installation and check versions after starting the VM:

🔍 To check Docker installation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Open a terminal in the VM and run

.. code-block:: bash

   docker --version

You will see output like:

.. code-block:: bash

   Docker version 28.1.1, build 4eba377

🔍 To check Docker Compose
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: bash

   docker compose version

.. note::
  docker compose (with a space) is used in recent versions instead of the older docker-compose command.

You will see output like:

.. code-block:: bash

   Docker Compose version v2.35.1

MongoDB Compass
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
It provides a user-friendly interface to visualize, query, and manage MongoDB databases. It simplifies database interaction by eliminating the need for manual command-line operations.

.. note::
  The pre-installed version of the MongoDB Compass is 1.40.4

🔍 Check MongoDB Compass
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

  * Open MongoDB Compass from the Applications menu.

  * Verify that the application launches successfully.

📥 Importing Docker Images into the VM
---------------------------------------

You are provided with pre-built Docker images in a .tar format, you can load them into Docker inside the virtual machine using the docker load command.

📁 Transfer the Docker Image Files
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Ensure the image files (mentioned in Prerequisite section) are available inside the VM. You can:

  * Drag and drop the file into the VM (if supported by VMware).

  * Use shared folders to transfer from host to VM.

  * Use scp or USB devices as alternatives.

      * check status

      .. code-block:: bash
        
         sudo systemctl status ssh
      

🐳 Load the Image into Docker
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Once the .tar files are accessible inside the VM, open a terminal and run

.. code-block:: bash

   cd <path-to-tar-files-folder>
   docker load -i asvin-rbc-portal.tar
   docker load -i asvin-rbc-device-service.tar
   docker load -i asvin-rbc-mongo.tar

✅ Verify the Image is Loaded
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Check the list of available Docker images:

.. code-block:: bash

  docker images

You will see output like this:

.. code-block:: bash

  REPOSITORY                 TAG       IMAGE ID       CREATED         SIZE
  asvin-rbc-portal           latest    d9d847a29288   2 weeks ago     48.4MB
  asvin-rbc-device-service   latest    58f9516cda65   2 weeks ago     861MB
  mongo                      6.0.6     7e32c3979b02   22 months ago   653MB


You should see the newly imported image listed.


🔧 Configuring Ports, Environment Variables and Volumes in Docker Compose
---------------------------------------

In the docker-compose.yml(Link)  file, you can easily configure port mappings, environment variables and volumes for the services.

#. Port Configuration

Use the ports field to map a port inside the container to a port on your virtual machine. The format is <host_port>:<container_port>. By default the service run on following ports.

  * Portal : 8080

  * Device Service: 5001

  * MongoDB: 27001

#. Environment Variable Configuration

Use the environment field to set environment variables inside the container. The environments variables are to used to configure the services. The configuration for various services are following.

.. note::
  
  Change the default username and password for MongoDB root user before deploying the application.

MongoDB 

    MONGO_INITDB_ROOT_USERNAME: Specifies the username for the MongoDB root user.
    MONGO_INITDB_ROOT_PASSWORD:Specifies the password for the MongoDB root user.

    Device Service

        MongoConnection__ConnectionString: Defines the full connection string used by the application to connect to the MongoDB server. It is defined in specific format, mongodb://username:passwrod@mongodb-host:mongodb-port/?authSource=admin

        MongoConnection__Database: Specifies the name of the MongoDB database that the application will use.

        JsonWebTokenKeys__IssuerSigningKey: Provides the secret key used to sign and validate JSON Web Tokens (JWTs) for authentication and authorization.

#. Persistent volume configuration

To ensure that MongoDB data remains persistent across container restarts, a Docker volume is configured for storage. This prevents data loss when containers are recreated, updated, or stopped.

The volume is defined under the volumes section of the docker-compose.yml file. By default, the database files are stored inside a local folder named rbc-data, located in the same directory as the Compose file.

You can customize the storage location by modifying the following line in the Compose file:

.. code-block:: bash
  
  volumes:
        - ./rbc-data/context:/data/db

Here, the path before the colon (./rbc-data/context) refers to the host machine directory, and /data/db is the internal path inside the MongoDB container where the data is stored.

🚀 Starting the Application with Docker Compose
---------------------------------------------------------------

The application is containerized and orchestrated using Docker Compose, which manages the frontend, backend, and database services.

📁 Navigate to the Project Directory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Open a terminal inside the virtual machine and move to the directory where the docker-compose.yml file is located:

.. code-block:: bash

  cd ~/project-directory 

🧱 Start the Application
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Use the following command to build (if needed) and start all services:
  
.. code-block:: bash
  
  docker compose up -d
 

* -d runs the services in the background (detached mode).

* Docker Compose will automatically:

  * Start the Portal (Angular)

  * Start the device service (.NET)

  * Start the database (MongoDB)

🔍 Verify Running Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Check the status of all services:

.. code-block:: bash

  docker compose ps

You should see the containers for portal, devicee service, and database marked as Up.

🌐 Access the Portal
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Open a browser inside the VM or from the host (if port forwarding is enabled) and go to: http://localhost:8080

.. note::

You can change the port in your docker-compose.yml.

🛑 Stopping the Application
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To stop all services when you're done:

.. code-block:: bash

  docer compose down

This will stop and clean up all running containers.

🖥️ Connecting to MongoDB Using MongoDB Compass
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

MongoDB Compass is a graphical interface that allows you to easily connect to your database, explore collections, and run queries without using the command line. Follow the steps below to connect to your MongoDB instance.
#. Open MongoDB Compass

    Launch the MongoDB Compass application.

#. Enter Connection Details

In the New Connection window, fill in the following details:

    Connection String: mongodb://username:passwrod@mongodb-host:mongodb-port/?authSource=admin

.. note:: 

Replace the username, password, host and port accordingly. 

#. Connect and Explore

    Click Connect to establish the connection.

    Once connected, you will see a list of databases on the left sidebar.

    Select your database (e.g., rbc) to view its collections and documents.