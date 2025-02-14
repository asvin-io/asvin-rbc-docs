============================
Config Contextual Parameters
============================
The Risk by Context™ Frontend allows users to configure contextual parameters at both the **segment** and **device** levels via the settings page. These parameters can significantly impact the risk posture of an OT environment. Each parameter consists of three key characteristics **Visibility**, **Threshold**, and **Relevance**. Understanding and setting these characteristics appropriately will allow for optimized risk assessment.

This document provides a detailed guideline on how to set and configure these contextual parameters 
efficiently.

Contextual Parameters Characteristics
-------------------------------------
When setting contextual parameters, you will need to configure the following characteristics:

#. **Visibility**: Defines whether a parameter is enable or disabled in the RBC-Index calculation.
    
    * `Checked`: The parameter is enabled in the settings UI and will be used in the RBC-Index calculation.
    
    * `Unchecked`: The parameter is disable in the UI will not be used in the RBC-Index calculation.

#. **Threshold**: The threshold determines the operational limits or boundaries for a given parameter. It is always numeric.
    
    * `0`: The lowest acceptable value for the parameter.
    
    * `any numeric value`: The highest acceptable value for the parameter.
    
    * `0`: The default value assigned when no specific configuration is set.

#. **Relevance**: This characteristic defines the parameter’s relevance to the OT environment for risk assessment. It determines how important a parameter is in the RBC-Index calculation.
    - `100`: The parameter is highly relevant.
    - `0`: The parameter is not relevant.

How to Set Contextual Parameters
--------------------------------
To set contextual parameters at the segment and device levels, follow the steps below. The Settings page is user-friendly and offers intuitive GUI for configuration.

.. raw:: html

  <video width="710" autoplay muted loop>
  <source src="../_static/videos/set-context-parameters.m4v" type="video/mp4">
  Your browser does not support the video tag.
  </video>


#. Access the Settings Page: Navigate to the **Settings Page** from side menu by clicking on **Settings** where you can manage the segment and device configurations. The **Settings** page has two primary areas:
    
    * **Segment Settings**: Parameters related to the network segments.

    * **Device Settings**: Parameters related to the devices in use.

#. Select the Parameter: Once you are on the settings page, find the parameter you wish to configure.

#. Modify the Characteristics of the Parameter: Each parameter will have an editable configuration section where you can set the **Visibility**, **Threshold**, and **Relevance** characteristics.

    * Set Visibility: Use the checkbox to control whether the parameter is enable or disable.
  
    * Set Threshold: **Threshold** can typically be set using text input for numeric values.

      For example:
       * **CVSS Score (Threshold)**: Set the value to 10.

    * Set Relevance: The **Relevance** slider allows you to specify how relevant the parameter is to the RBC-Index of a segment or device configuration.
       
       * **1oo**: The parameter is highly relevant.
       
       * **0**: The parameter is not relevant.
       
      For example:
       * **Internal network connections**: Set to `27%`.

#. Save the Configuration: Once you have set the **Visibility**, **Threshold**, and **Relevance** for the parameter, click the **Save** button to persist the changes.

#. Verify the Settings: After saving the configurations, verify that the contextual parameters are applied correctly:

    * **Test Visibility**: If the parameter is set to **Enable**, it should appear green in the settings UI. If it is set to **Disable**, checkbox should appear empt in the UI.
    
    * **Test Threshold**: Check the threshold is set to the desired numeric value.
    
    * **Test Relevance**: Check the relevant is set to the specified value.

Example of Setting Parameters in the UI
---------------------------------------
Here’s an example of setting contextual parameters in the settings page for a **Operational 
significance** parameter:

1. **Visibility**: Set to **Visible**.
2. **Threshold**:  Set to 4.
3. **Relevance**: Set to **34%**.

These settings will ensure that the **Operational significance** parameter is visible, has a threshold value of 4, and is `34%` relevant in the context based risk assessment.

Best Practices
--------------
#. **Set Meaningful Threshold Value**: Always define suitable **Threshold** values for parameters to ensure optimal performance for your OT environment.

#. **Relevance Should Reflect Context**: Ensure the **Relevance** of parameters aligns with actual usage conditions of OT environment for the best results.

Conclusion
----------
By following the above steps, you can efficiently set contextual parameters in Risk by Context™ at both the segment and device levels. Understanding how to configure **Visibility**, **Threshold**, and **Relevance** will ensure that parameters are properly adjusted according to the device or segment conditions, providing a tailored experience for risk assessment for your OT environment.

