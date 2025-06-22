===============
RBC CLI Utility
===============

A Bash utility script to manage Risk by Context™ solution containers.

Prerequisites
-------------

Before using the :term:`RBC CLI` utility, ensure the following dependencies are installed and properly configured on your system:

- **Docker**: Required to manage and run containerized applications.
- **Docker Compose**: Needed for defining and running multi-container Docker applications.

Make sure both Docker and Docker Compose are accessible from your command line before proceeding. You can verify using the following commands.

.. code-block:: bash

   docker version
   docker compose version

Usage
-----

.. code-block:: bash

   ./rbc [OPTIONS] COMMAND [ARGS]

Options
-------

* ``-h``  
  Show this help message and exit.

* ``-v``  
  Show version.

* ``-d``  
  Enable debug mode.

Commands
--------

The :term:`RBC CLI` provides a set of commands to manage and operate RBC containers efficiently.

.. warning::

   Ensure that the :code:`docker-compose.yml` file exists in the directory where you run the :code:`ps`, :code:`up`, :code:`down`, :code:`restart` and :code:`upgrade` commands.

.. warning::

   The :code:`./rbc load` command depends on the presence of the required ``.tar`` files. If these files are missing, the command will fail to load the Docker images.

**load <name>**
^^^^^^^^^^^^^^^
Load Docker images by name.

Supported values:

* *(empty)*  : Load all images
* ``portal`` : Load the Portal image
* ``device`` : Load the Device service image
* ``mongo``  : Load the MongoDB image

**ps**
^^^^^^
Show status of all RBC containers.


**up <name>**
^^^^^^^^^^^^^
Create and start Docker containers.

Supported values:

* *(empty)*  : Start all containers
* ``portal`` : Start the Portal container
* ``device`` : Start the Device service container
* ``mongo``  : Start the MongoDB container

**down <name>**
^^^^^^^^^^^^^^^ 
Stop and remove Docker containers.

Supported values:

* *(empty)*  : Stop all containers
* ``portal`` : Stop the Portal container
* ``device`` : Stop the Device service container
* ``mongo``  : Stop the MongoDB container

**restart <name>**
^^^^^^^^^^^^^^^^^^
Remove and create Docker containers.

Supported values:

* *(empty)*  : Remove and create all containers
* ``portal`` : Remove and create the Portal container
* ``device`` : Remove and create the Device service container
* ``mongo``  : Remove and create the MongoDB container
  
**upgrade <name>**
^^^^^^^^^^^^^^^^^^
Load docker image and remove & create Docker containers.

Supported values:

* *(empty)*  : Upgrade all containers
* ``portal`` : Upgrade the Portal container
* ``device`` : Upgrade the Device service container
* ``mongo``  : Upgrade the MongoDB container

Examples
--------

.. code-block:: bash

   ./rbc load portal
   ./rbc up device
   ./rbc restart
   ./rbc upgrade

.. _rbc-cli-errors:

Common Errors
-------------

.. tip::
   
   If this section doesn not resolve your issue, feel free to create a new issue in the `asvin RBC repository <https://github.com/asvin-io/asvin-rbc-docs/issues>`_ or contact us at :code:`info@asvin.io`.

Below are common errors you might encounter while using the :term:`RBC CLI` utility.

.. error:: `./rbc: No such file or directory`

   This error occurs when the :code:`rbc` file does not exist in the current directory.
   
   **Solution:**

   Download the :term:`RBC CLI` from :download:`here <../_static/code/rbc>`.

.. error:: `bash: ./rbc: Permission denied`

   This error occurs when the file lacks execute permissions. You can fix 
   
   **Solution:**

   Provide execute permission by running :code:`chmod +x rbc` in :term:`Terminal`.

.. error:: `./rbc: unrecognized option: --foo`

   This error means you passed an invalid option.

   **Solution:**
   
   Run :code:`./rbc -h` to see all supported options.

.. error:: `./rbc: unrecognized command: --foo`

   This error means you passed an invalid command.
   
   **Solution:**

   Run :code:`./rbc -h` to see all supported commands.

.. error:: `./rbc docker-compose.yml not found.`

   This error occurs when the :code:`docker-compose.yml` file is missing from the current directory. 
   
   **Solution:**

   Download the file from :download:`here <../_static/code/docker-compose.yml>`
