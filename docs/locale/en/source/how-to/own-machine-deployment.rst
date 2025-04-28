
====================================
On-Premise deployment on Own Machine
====================================

This method describes how to manually install and configure all required components for Risk by Context™ on a physical or virtual machine. It is recommended for users who require greater flexibility, customization, or wish to integrate the system into existing infrastructure.

asvin provides pre-built docker images for Risk by Context™ to run in containers.

System Requirements
-------------------
Hardware
^^^^^^^^
  * 2 GHz dual-core processor
  * 3D acceleration-capable GPU with at least 256 MB of VRAM
  * 4 GB RAM (Recommended 8 GB or more)
  * 50 GB hard-drive space

Software
^^^^^^^^
To install Risk by Context™  successfully, your machine must meet the following software requirements.

Operating System
""""""""""""""""
    
* Ubuntu 22.04 LTS

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
Install `Docker Engine <https://docs.docker.com/engine/install/>`_ or `Docker Desktop <https://docs.docker.com/desktop/>`_. 

Deployment steps
----------------
.. note::
   Check with your IT administrator for network security configuration before the deployment.

#. Check if docker engine is installed with :code:`docker version & docker compose version` and you are able to run :code:`docker run hello-world` without errors.
#. Run RBC containers :ref:`using docker<start-using-docker>`  or :ref:`using docker compose<start-using-docker-compose>` 
#. Verify if containers are running with :code:`docker ps -a` or :code:`docker compose ps -a`
#. Access the Risk by Context™ Portal in your browser at `http://localhost:8080 <http://localhost:8080/>`_
