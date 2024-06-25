## Kubernetes-Based MongoDB and Mongo Express Deployment

#### Project Description:

This project showcases the deployment of a MongoDB database and a Mongo Express web interface as containerized applications within a Kubernetes cluster. The setup utilizes Kubernetes ConfigMaps and Secrets for managing configurations and sensitive data securely. The primary objective is to demonstrate the deployment, configuration, and management of a scalable database solution and its web interface using Kubernetes.

#### Project Details:

**Objective:**
To deploy a MongoDB database and Mongo Express web interface on a Kubernetes cluster, ensuring secure and efficient management of configuration and credentials through Kubernetes ConfigMaps and Secrets.

**Components:**

1. **MongoDB Deployment:**
    - **Deployment Configuration (`mongo-app.yaml`):**
        - Uses the `mongo:8.0` Docker image.
        - Configures the initial root username and password from Kubernetes Secrets.
        - Exposes MongoDB on port 27017.
    - **Service Configuration (`mongo-app.yaml`):**
        - Creates a ClusterIP service for MongoDB to enable internal communication within the cluster.

2. **Mongo Express Deployment:**
    - **Deployment Configuration (`web-app.yaml`):**
        - Uses the `mongo-express:1.0` Docker image.
        - Configures Mongo Express to authenticate users using credentials stored in Kubernetes Secrets.
        - Connects Mongo Express to MongoDB using the service name provided in a Kubernetes ConfigMap.
        - Exposes Mongo Express on port 8081.
    - **Service Configuration (`web-app.yaml`):**
        - Creates a NodePort service to expose the Mongo Express UI to external traffic on port 30010.

3. **Kubernetes ConfigMap and Secrets:**
    - **ConfigMap (`mongo-config.yaml`):**
        - Stores the MongoDB service URL.
    - **Secret (`secret.yaml`):**
        - Stores the MongoDB root username and password in Base64 encoded format.

**Project Workflow:**

1. **Create Kubernetes Secrets:**
    - Encode the MongoDB username and password in Base64 and store them in a Kubernetes Secret.

2. **Create Kubernetes ConfigMap:**
    - Store the MongoDB service URL in a Kubernetes ConfigMap for easy reference in the Mongo Express deployment.

3. **Deploy MongoDB:**
    - Define and apply the MongoDB Deployment and Service configurations to create a MongoDB pod and expose it within the cluster.

4. **Deploy Mongo Express:**
    - Define and apply the Mongo Express Deployment and Service configurations to create a Mongo Express pod and expose its UI externally.

5. **Access Mongo Express:**
    - Use the NodePort service to access the Mongo Express web interface and interact with the MongoDB database.

**Key Features:**
- **Scalability:** Leverages Kubernetes capabilities to scale the MongoDB and Mongo Express deployments as needed.
- **Security:** Utilizes Kubernetes Secrets to manage sensitive information such as database credentials securely.
- **Configuration Management:** Employs Kubernetes ConfigMaps to manage and inject configuration data into the containers.
- **Portability:** Ensures that the deployment is portable across different environments that support Kubernetes.

**Outcome:**
Successfully deployed and configured a MongoDB database and a Mongo Express web interface on a Kubernetes cluster, providing a robust and scalable solution for database management and administration.

This project demonstrates the effective use of Kubernetes for deploying containerized applications, in a cloud-native environment.