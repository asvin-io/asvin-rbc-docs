================
On-premise Deployment
================

Prerequisites
---------------------

Before proceeding with the setup, ensure the following requirements are met:

Hardware Requirements
---------------------
  * A 64-bit processor with virtualization support (Intel VT-x or AMD-V).

  * Minimum 4 GB RAM (8 GB recommended).

  * Minimum 50 GB free disk space.

  * At least 2 CPU cores (4 recommended).

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

Download Files
^^^^^^^^^^^^^^^
  * Ensure you have access to the following files

    * virtual machine image (.ova)

      * docker images

            Portal:  asvin-rbc-portal.tar

            Backend: asvin-rbc-device-service.tar

            Database: asvin-rbc-mongo.tar

      * docker-compose.yml file

🛠️ Setup Guide: Importing the OVA File into VMware
---------------------------------------------------------------

  Follow the steps below to import the provided .ova file into your VMware application.

    * Please install all the required tools and download images as described in Prerequisite setup.


Launch VMware
^^^^^^^^^^^^^^^
Open the VMware application:

  * On Windows/Linux: Open VMware Workstation or VMware Player.
  * On macOS: Open VMware Fusion.
 
Import the OVA File
^^^^^^^^^^^^^^^^^^^^
    From the main menu, select File → Open.

    Browse to the location of the .ova file provided (e.g., asvin-rbc.ova).

    Select the .ova file and click Open.

    VMware will display an Import Virtual Machine window.

    Choose a name and destination folder for the virtual machine.

    Click Import to begin the process.

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

  * Docker is installed to support containerized applications.

  * Docker Compose is available to orchestrate multi-container services.

You can verify the installation and check versions after starting the VM:

🔍 To check Docker installation:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Open a terminal in the VM and run:
  
  docker --version

🔍 To check Docker Compose:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
docker compose version

docker compose (with a space) is used in recent versions instead of the older docker-compose command.

📥 Importing Docker Images into the VM
------------------------------------------

You are provided with pre-built Docker images in a .tar format, you can load them into Docker inside the virtual machine using the docker load command.

📁 Transfer the Docker Image Files
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Ensure the image files (mentioned in Prerequisite section) are available inside the VM. You can:

  * Drag and drop the file into the VM (if supported by VMware).

  * Use shared folders to transfer from host to VM.

  * Use scp or USB devices as alternatives.

🐳 Load the Image into Docker
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Once the .tar files are accessible inside the VM, open a terminal and run

  cd <path-to-tar-files-folder>
  docker load -i asvin-rbc-portal.tar
  docker load -i asvin-rbc-device-service.tar
  docker load -i asvin-rbc-mongo.tar

✅ Verify the Image is Loaded
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Check the list of available Docker images:

  docker images

You should see the newly imported image listed.

🚀 Starting the Application with Docker Compose
---------------------------------------------------------------

The application is containerized and orchestrated using Docker Compose, which manages the frontend, backend, and database services.

📁 Navigate to the Project Directory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Open a terminal inside the virtual machine and move to the directory where the docker-compose.yml file is located:
  
  cd ~/project-directory 

🧱 Start the Application
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Use the following command to build (if needed) and start all services:
  
  docker compose up -d 

   * -d runs the services in the background (detached mode).

   * Docker Compose will automatically:

      * Start the Portal (Angular)

      * Start the device service (.NET)

      * Start the database (MongoDB)

🔍 Verify Running Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Check the status of all services:
  
  docker compose ps

You should see the containers for portal, devicee service, and database marked as Up.

🌐 Access the Portal
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Open a browser inside the VM or from the host (if port forwarding is enabled) and go to: http://localhost:8080

You can change the port in your docker-compose.yml.

🛑 Stopping the Application
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To stop all services when you're done:

  docer compose down

This will stop and clean up all running containers.