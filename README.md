
# SkyServe CLI Tutorial

## Introduction

Welcome to the comprehensive guide on using the SkyServe Command Line Interface (CLI) for managing multi-region, multi-cloud services. SkyServe CLI streamifies the process of deploying, updating, monitoring, and tearing down your services across various cloud providers, ensuring you can focus on building high-quality applications.

This tutorial aims to equip you with a solid understanding of SkyServe CLI's capabilities, covering everything from initial setup to advanced monitoring techniques. By the end of this guide, you'll be proficient in leveraging SkyServe to enhance your cloud service management workflow.

| Command                                         | Description                                               | Purpose                                                 | Metadata                |
|-------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------|-------------------------|
| `sky serve up main.yaml`                                  | Launch a SkyServe service.                                | To deploy a new service or application.                 | Initial deployment.     |
| `sky serve update`                              | Update a SkyServe service.                                | To apply updates or changes to an existing service.     | Updates and maintenance.|
| `sky serve status <service-name>`               | Show detailed info about the service.                     | To check the current status and health of a service.    | Monitoring.             |
| `sky serve down <service-name>`                 | Teardown the specified service.                           | To remove and clean up resources of a service.          | Cleanup.                |
| `sky serve logs <service-name> [REPLICA_ID]`    | Show logs for a specific replica of the service.          | To diagnose issues or monitor the activity of a service.| Debugging.              |
| `sky serve logs --load-balancer <service-name>` | Show logs for the load balancer of the service.           | To check the load balancer's activity and performance.  | Monitoring.             |
| `sky serve logs --controller <service-name>`    | Show logs for the controller of the service.              | To monitor the control plane's operations.              | Monitoring.             |
| `watch -n10 sky serve status <service-name>`    | Monitor the status of the service, updating every 10 sec. | To continuously observe the service's health.            | Real-time monitoring.   |
| `curl -L <endpoint URL>`                        | Send a test request to the service's endpoint.            | To verify the service is operational and reachable.      | Testing and verification.|

Each command serves a specific role in the lifecycle and management of services deployed using the SkyServe CLI, from deployment to teardown. This table aims to offer a quick reference to understand the capabilities and purposes of various commands within the SkyServe ecosystem.

## Getting Started

### Prerequisites

Before diving into the SkyServe CLI, ensure you have the following prerequisites:

- A basic understanding of command line interfaces.
- Access to a terminal or command prompt.
- An account with a supported cloud service provider (e.g., AWS, Google Cloud, Azure).

### Installation

To install SkyServe CLI, run the following command in your terminal:

```sh
pip install -U skypilot
```

This command downloads and installs the latest version of SkyServe CLI, adding it to your system's PATH for easy access.

### Configuration

After installation, configure SkyServe CLI with your cloud provider credentials. This process varies by provider but generally involves setting environment variables or using a configuration file.

For example, to configure AWS credentials:

```sh
export AWS_ACCESS_KEY_ID="your_access_key"
export AWS_SECRET_ACCESS_KEY="your_secret_key"
```

Refer to the SkyServe documentation for detailed instructions on configuring your specific cloud provider.

## Deploying Your First Service

Deploying a service with SkyServe CLI is straightforward. This section walks you through the process of deploying a simple "Hello World" application.

### Preparing Your Application

Ensure your application is containerized and uploaded to a container registry accessible by your cloud provider. For this tutorial, we'll assume you have a Docker image named `hello-world:latest`.

### Launching the Service

To launch your service, use the `sky serve up` command:

```sh
sky serve up --name hello-world-service --image hello-world:latest
```

This command deploys your `hello-world` application as a service named `hello-world-service`. SkyServe takes care of the underlying infrastructure, such as provisioning servers and configuring load balancers.

### Verifying Deployment

After deployment, verify your service is running:

```sh
sky serve status hello-world-service
```

This command displays the status of your service, including its endpoint URL.

## Monitoring and Logs

Monitoring your services and accessing logs are crucial for maintaining healthy applications. SkyServe CLI provides commands to facilitate these tasks.

### Accessing Logs

To view logs for a specific replica of your service:

```sh
sky serve logs hello-world-service [REPLICA_ID]
```

For logs from the load balancer or controller:

```sh
sky serve logs --load-balancer hello-world-service
sky serve logs --controller hello-world-service
```

### Continuous Monitoring

For real-time monitoring, use the `watch` command:

```sh
watch -n10 sky serve status hello-world-service
```

This setup refreshes the status of your service every 10 seconds, allowing you to monitor its health continuously.

## Updating Your Service

SkyServe CLI makes it easy to update your service, whether applying a new image or scaling resources.

### Applying a New Image

To update your service with a new image:

```sh
sky serve update --name hello-world-service --image hello-world:new-version
```

This command deploys the new image across your service, ensuring zero downtime with rolling updates.

### Scaling Your Service

Adjust the number of replicas for your service:

```sh
sky serve update --name hello-world-service --replicas 3
```

This increases the number of running instances of your service to three, improving its availability and load capacity.

## Teardown and Cleanup

When you no longer need your service, SkyServe CLI offers a simple command to tear it down:

```sh
sky serve down hello-world-service
```

This command removes all resources associated with your service, including servers, load balancers, and network configurations, ensuring you're not billed for unused resources.

## Conclusion

SkyServe CLI is a powerful tool for managing your cloud-based services across multiple regions and providers. This tutorial covered the basics of deploying, monitoring, updating, and tearing down services with SkyServe. However, the capabilities of SkyServe extend far beyond what's covered here. Explore the SkyServe documentation for more advanced features, including service discovery, auto-scaling, and cross-cloud deployments.

Remember, practice is key to mastering SkyServe CLI. Experiment with different configurations, monitor your services closely, and don't hesitate to use the help command (`sky serve -h`) to explore all available options.

