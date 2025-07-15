=============
Add Interface
=============
Risk by Context™ framework supports a range of interfaces designed to seamlessly pull contextual data from diverse sources and push actionable risk insights to decision-making systems such as Security Operations Centers (SoCs). These interfaces enable real-time data ingestion from various environments—including asset management system, vulnerability management system, directory services—ensuring a comprehensive understanding of network topology, vulnerabilities and operational conditions. By integrating with existing security ecosystems, the RBC interfaces facilitate automated, informed, and timely responses to emerging threats, thereby enhancing situational awareness and accelerating risk mitigation efforts.

Adding a New Interface
----------------------

To add a new interface in the Asvin RBC platform, follow the steps below:

1. **Navigate to the Interface Section**

   In the side menu, click on **Interfaces** to open the interface management view.

2. **Add a New Interface**

   Click on the **Add New Interface** Tab to begin the configuration process.

3. **Select Interface**

  From the list of available interface types, select the one you wish to add. A configuration pop-up window will appear.

4. **Configure Interface Settings**

   In the pop-up window, provide the following details:

   - **Name**: A descriptive name for the interface.
   - **Base URL**: The endpoint URL of the data source or destination system.
   - **API Key**: The authentication token required to access the interface securely.

5. **Test the Connection**

   Click on **Test** to validate the provided settings. Ensure the connection is successful before proceeding.

6. **Save the Interface**

   Once the connection test passes, click **Add** to register and activate the new interface.


.. raw:: html

  <video width="710" autoplay muted loop>
  <source src="../_static/videos/add-interface.m4v" type="video/mp4">
  Your browser does not support the video tag.
  </video>


The newly added interface will now be listed and ready for use in context data ingestion or risk insight delivery workflows.
