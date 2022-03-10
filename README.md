# cross-namespace-gateway-routing-in-GKE

Gateway - overcoming GCP Ingress limitations
While exposing applications in GKE, often we create a GKE Ingress object, which creates a load balancer and routing rules in the backend to expose your application.
But in scenarios like many users or teams is sharing the underlying networking infrastructure, control, and configuration, which must be segmented to minimize access and fault domains.
For such use-cases, it has some limitations -
For ingress objects, the load balancer & its routing rules are created in a combined manner.
We cannot map multiple services in different namespaces in a single GKE ingress object.
Mapping of different DNS or hostname of different ingress can't be bound with the same single IP address.

Gateway is the solution to overcome these limitations & you just need to create a Gateway object in place of Ingress.
The Gateway API has core support for cross Namespace routing. It uses separate Gateways and Route resources, to deploy load balancers and routing rules. This differs from Ingress, which combines everything in one resource.
By splitting responsibility among resources, Gateway enables the load balancer and its routing rules to be deployed separately and to be deployed & managed by different users or teams across Namespace boundaries.

