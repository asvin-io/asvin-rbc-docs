
==============================================
Deploymet on a Kubernetes Cluster in the Cloud
==============================================
This chapter outlines the steps required to deploy the asvin Risk by Context™ solution on a cloud-based Kubernetes cluster. The deployment process ensures scalability, high availability, and efficient orchestration of RBC microservices within a managed Kubernetes environment (e.g., AWS EKS, Azure AKS, or Google GKE).

Prerequisites
-------------

Before deploying asvin RBC, ensure the following prerequisites are met:

- Access to a cloud provider account (AWS, Azure, or GCP)
- A configured Kubernetes cluster (minimum version: 1.21)
- `kubectl` CLI installed and configured
- Docker image registry credentials (if using a private registry)
- Persistent storage class configured in the cluster

Architecture Overview
---------------------

Asvin RBC is composed of several modular microservices, including:

- :term:`RBC Portal`: Web-based frontend for configuration and monitoring.
- :term:`RBC Engine`: Collects contextual data from external interfaces, Computes and prioritizes risk scores, Manages connectors to data sources and destinations, Pushes insights to external systems such as SoC
- Database: NonSQL database to store contextual data

Each service runs in its own container, orchestrated via Kubernetes deployments.

Deployment Steps
----------------

1. :download:`asvin-rbc-k8s.yaml <../_static/code/asvin-rbc-k8s.yaml>`


2. **Update Configuration Files**

   Edit the `yaml` file to match your cloud and network configuration. Set:

   - `image.repository` and `image name`
   - Resource limits for CPU and memory
   - External interface API keys

3. **Deploy RBC Services**

   Deploy each service using the Helm charts provided:

   .. code-block:: bash

      kubectl apply -f asvin-rbc-k8s.yaml

   Monitor deployments:

   .. code-block:: bash

      kubectl get pods -n asivn-rbc

4. **Expose the UI and APIs**

   Use a Kubernetes Ingress controller (e.g., NGINX) to expose the :term:`RBC Portal` and :term:`RBC Engine` to external users. Set the domain name in the ingress configuration in the `yaml` file.

5. **Verify Deployment**

   - Open the UI in a browser at `https://rbc.example.com`
   - Check logs for each service:

     .. code-block:: bash

        kubectl logs <pod-name> -n asvin-rbc

   - Use the dashboard to verify that interfaces can be configured and risk insights are generated.

Security Considerations
-----------------------

- Use Kubernetes secrets to store sensitive values such as API keys and passwords.
- Apply network policies to restrict service-to-service communication.
- Enable TLS for all external access via Ingress.
- Monitor and audit access using tools like Prometheus, Grafana, and Falco.

Conclusion
----------

Deploying asvin RBC on a Kubernetes cluster enables scalable, modular, and resilient risk communication capabilities in cloud environments. For production-grade setups, consider using managed Kubernetes services with autoscaling, logging, and security policies in place.