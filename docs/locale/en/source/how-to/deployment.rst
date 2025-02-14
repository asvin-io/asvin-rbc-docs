================
Deployment Model
================
Risk by Context™ supports both **On-Premise** and **SaaS** deployment model. Organizations can choose the appropriate deployment model based on their specific requirements for data control, scalability, and security. On-Premise Deployment provides full control over infrastructure and security, SaaS Deployment offers a managed, scalable cloud-based solution,

On-Premise Deployment
---------------------
asvin provides docker images for Risk by Context™ to run in containers.

System Requirements
^^^^^^^^^^^^^^^^^^^^
* Hardware

  * CPU: 4-core (Intel/AMD) 2.5 GHz or higher

  * RAM: 8 GB

  * Storage: 50 GB SSD

  * Network: 1 Gbps Ethernet

* Software:

  * Operating System: Ubuntu 22.04 LTS or later / Windows with WS2

  * Containerization: `Docker Engine <https://docs.docker.com/engine/install/>`_ 26+ or Kubernetes (Optional for scaling)

Deployment steps
^^^^^^^^^^^^^^^^
.. note::
   Check with your IT administrator for network security configuration before the deployment.

#. Prepare the Environment

    * Check if docker engine is installed with :code:`docker version & docker compose version`

    * Configure firewall rules and network security groups

#. Install RBC Components using :ref:`docker<start-using-docker>`  or :ref:`docker compose<start-using-docker-compose>` 

#. Verify if container are running with or :code:`docker ps -a` :code:`docker compose ps -a`

#. Access the Risk by Context™ Frontend in your browser on `http://localhost:8080 <http://localhost:8080/>`_
