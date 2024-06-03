## Milestone 5: Deploying Multi-Architecture ECS Service

### Overview
In this milestone, we delve into the realm of multi-architecture images, powered by Docker manifests. Docker manifests serve as a mechanism for amalgamating multiple architecture-specific images into a singular "meta" image, supporting diverse architectures seamlessly. With the emergence of ARM64 and the introduction of AWS Graviton offerings, customers now have the opportunity to capitalize on ARM64 for potential cost savings. However, a crucial question arises: how can customers effortlessly ensure their applications function seamlessly on ARM64?

Enter the concept of multi-architecture images. In this milestone, we embark on the journey of constructing such images, enabling us to harness the power of both AMD64 and ARM64 architectures.

In addition to manually deploying the ECS service, we ensure that the CircleCI configuration is updated to reflect the inclusion of the new ARM64 service. This enables us to test and deploy both ARM64 and AMD64 architectures seamlessly with each run of our CI/CD workflow.

### Steps
1. **Update CircleCI Configuration:**
   - Modify the CircleCI configuration to incorporate the new ARM64 service information.
   - Ensure that the CircleCI workflow now includes steps for testing and deploying both ARM64 and AMD64 architectures.

3. **Verify Architecture and Docker Image Location:**
   - Navigate to the DNS name of the load balancer.
   - On the website, observe the architecture displayed.
   - Scroll down to the bottom of the demo app and click on "build info" to access further information about the architecture, build links to CircleCI, and build triggers.

### Objectives
- Deploy a new ECS service, selecting the appropriate ARM64 task definition.
- Update the CircleCI configuration to accommodate the new ARM64 service, allowing for testing and deployment of both ARM64 and AMD64 architectures.
- Verify the architecture and Docker image location by accessing the DNS name of the load balancer and inspecting the website.