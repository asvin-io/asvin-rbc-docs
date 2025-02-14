================
Risk Assessment
================

Cyber risk refers to the potential for financial loss, operational disruption, or reputational damage due to cyber threats such as malware, ransomware, data breaches, and system vulnerabilities. Managing cyber risk is critical for securing OT infrastructures against evolving threats.

Cyber Risk Assessment Factors
-----------------------------
Risk by Context™ evaluates risk based on two key factors, Likelihood and Impact.

Likelihood
^^^^^^^^^^
It involves probability of exploiting a cyber risk. We look it from two parameters

#. Reachability: How easily an attacker can access the target (e.g., exposed services, network segmentation).

#. Difficulty: The complexity of exploiting a risk (e.g., security controls, authentication barriers).

A higher likelihood means an attack is more feasible and should be prioritized for mitigation.

Impact
^^^^^^
It involves assessement of the consequences if a risk is successfully exploited. Risk by Context™ measure it in following areas.

* Operational Impact: System downtime, production halts, supply chain disruptions.

* Financial Impact: Data loss, regulatory fines, legal penalties.

High-impact risks require immediate attention and stronger security measures.

Risk Assessment Process
-----------------------

#. Identify Devices in the OT Environment → Determine which systems, data, and operations require protection.

#. Collect Contextual Data → Gather relevant information about the identified devices, such as network segments, software versions, internal/external connections, and user roles.

#. Build a Knowledge Graph Using the Risk by Context™ Engine → Represent devices as nodes and their relationships as edges to visualize dependencies and risks.

#. Perform Risk Assessment → Evaluate the likelihood and impact of risks based on selected contextual parameters. Query the knowledge graph to generate an RBC-Index for each device.

#. Prioritize Risks → Rank devices based on their RBC-Index to focus on the most critical threats.

#. Generate Risk Insights → Provide actionable recommendations based on identified risks.

#. Continuous Monitoring → Continuously track and update risk assessments to maintain security over time.