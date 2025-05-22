===============
RBC CLI Utility
===============

A Bash utility script to manage Risk by Context™ solution containers.

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
