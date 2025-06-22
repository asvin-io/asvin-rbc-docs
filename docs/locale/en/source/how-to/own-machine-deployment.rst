
====================================
On-Premise deployment on Own Machine
====================================

This method describes how to manually install and configure all required components for Risk by Context™ on a physical or virtual machine. It is recommended for users who require greater flexibility, customization, or wish to integrate the system into existing infrastructure. asvin provides pre-built docker images for Risk by Context™ to run in containers.

System Requirements
-------------------
This section contains information about software and hardware requirements for installation of Risk by Context™ solution.

Hardware
^^^^^^^^

  * 4-core CPU
  * 4 GB RAM (Recommended 8 GB or more for smoother performance)
  * 50 GB hard-drive space

Software
^^^^^^^^
To install Risk by Context™ successfully, your machine must meet the following software requirements.

Operating System
""""""""""""""""
    
* Ubuntu

  * Ubuntu 22.04, 24.04, or the latest non-LTS version.
  * 64-bit kernel and CPU support for virtualization.
  * KVM virtualization support. To check if the KVM modules are enabled, execute :code:`lsmod | grep kvm`. You should see KVM related modules.
  * systemd init system

* Windows
  
  * WSL version 1.1.3.0 or later.
  * Windows 11 64-bit: Home or Pro version 22H2 or higher, or Enterprise or Education version 22H2 or higher.
  * Windows 10 64-bit: Minimum Home or Pro 22H2 (build 19045) or higher, or Enterprise or Education 22H2 (build 19045) or higher.
  * Enable the WSL 2 feature on your Windows system. For step-by-step guidance, refer to the official `Microsoft documentation <https://learn.microsoft.com/en-us/windows/wsl/install>`_.

Containerization technology: 
""""""""""""""""""""""""""""
.. warning::
   Docker can bypass firewall rules set by ufw or firewalld when exposing container ports. Review `Docker’s firewall behavior <https://docs.docker.com/engine/network/packet-filtering-firewalls/#docker-and-ufw>`_ before installing.

Install `Docker Engine <https://docs.docker.com/engine/install/>`_ or `Docker Desktop <https://docs.docker.com/desktop/>`_. 

Deployment steps
----------------
.. note::
   Check with your IT administrator for network security configuration before the deployment.

.. note::
   Check if docker is installed with :code:`docker version & docker compose version` and you can run :code:`docker run hello-world` without errors. 
 
#. Run RBC containers :ref:`using RBC CLI<start-using-rbc>`, :ref:`using docker compose<start-using-docker-compose>` or :ref:`using docker<start-using-docker>`  
#. Verify if containers are running with :code:`./rbc ps`, :code:`docker compose ps -a` or :code:`docker ps -a`
#. Access the :term:`RBC Portal` in your browser at `http://localhost:8080 <http://localhost:8080/>`_
