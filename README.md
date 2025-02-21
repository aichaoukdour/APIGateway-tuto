# API Gateway Overview

## What Does an API Gateway Do?

An API gateway serves as a single entry point for clients to access multiple backend services of an application. It sits between clients and these backend services, providing several crucial functions:

<img width="745" alt="image" src="https://github.com/user-attachments/assets/950de480-5c34-459f-8887-db1c3e351675" />

### 1. Authentication and Security
- Enforces authentication and security policies, validating requests.
- Checks IP addresses and headers against allow-lists and deny-lists.

### 2. Load Balancing and Circuit Breaking
- Distributes client requests across backend servers for optimal load distribution.
- Protects services from overload with circuit-breaking mechanisms.

### 3. Protocol Translation and Service Discovery
- Translates requests to match the protocols supported by backend services.
- Uses service discovery to locate and route requests to the appropriate service.

### 4. Monitoring, Logging, Analytics, and Billing
- Provides insights into API usage.
- Monitors performance, logs activities for auditing and debugging.
- Collects analytics for operational insights and tracks usage for billing purposes.

### 5. Caching
- Improves performance by storing responses to repeated requests.
- Serves cached responses when possible, reducing the load on backend services.

---

## Why Do We Need an API Gateway?

<img width="601" alt="image" src="https://github.com/user-attachments/assets/7b7b0116-8923-40a2-973d-c4c7fa04ea93" />

### 1. Centralized Management
- Simplifies API management by consolidating various functions into a single service.

### 2. Enhanced Security
- Secures backend services by enforcing authentication, authorization, and rate limiting at a single point.

### 3. Improved Performance
- Optimizes traffic flow with load balancing and caching.
- Reduces latency and enhances scalability.

### 4. Operational Insights
- Provides comprehensive monitoring, logging, and analytics.
- Improves operational visibility and helps with troubleshooting.

### 5. Protocol Flexibility
- Supports multiple protocols (e.g., REST, GraphQL).
- Handles protocol translation seamlessly.

## Conclusion
An API gateway is a critical component of modern application architecture, providing essential services like security, performance optimization, and operational monitoring. It simplifies the management of distributed systems by acting as a single entry point to multiple backend services.

---

# API Gateway Flow

## Step 1: Client Sends Request to API Gateway
<img width="717" alt="image" src="https://github.com/user-attachments/assets/36372088-b4d0-4d1f-9f29-9e549c59e04f" />

- The request is typically HTTP-based. It could be REST, GraphQL, or some other higher-level abstractions.

## Step 2: API Gateway Validates the HTTP Request
<img width="470" alt="image" src="https://github.com/user-attachments/assets/f8d23772-0b7c-4bc6-89ac-9ca00f349ce6" />

- The API gateway checks the validity of the incoming request.

## Step 3: API Gateway Checks Caller’s IP and HTTP Headers
<img width="605" alt="image" src="https://github.com/user-attachments/assets/c440c4f2-fb67-4fee-bb8b-e51688ed22c9" />

- The API gateway checks the caller’s IP address and other HTTP headers against its allow-list and deny-list.
- It could also perform basic rate limit checks against attributes such as IP address and HTTP headers.
  <img width="404" alt="image" src="https://github.com/user-attachments/assets/c5374826-69bc-44ae-a0a5-942c81a5b4b1" />

- For example, it could reject requests from an IP address exceeding a certain rate.

## Step 4: Request Passed to Identity Provider for Authentication and Authorization
<img width="599" alt="image" src="https://github.com/user-attachments/assets/756370eb-1c51-4194-a0e4-d3f40f84b221" />

- The API gateway passes the request to an identity provider for authentication and authorization.
- This is a complex process and may include checking user credentials, tokens, etc.
- The API gateway receives an authenticated session back from the provider with the scope of what the request is allowed to do.

## Step 5: Higher-Level Rate Limit Check
<img width="631" alt="image" src="https://github.com/user-attachments/assets/cd2366de-b8b0-491f-9e3c-99236a083692" />

- A higher-level rate limit check is applied to the authenticated session.
- If the request exceeds the limit, it is rejected at this point.

## Step 6 and 7: Service Discovery and Path Matching
<img width="617" alt="image" src="https://github.com/user-attachments/assets/267c7100-b421-44f3-804e-c88d675add82" />

- With the help of a service discovery component, the API gateway locates the appropriate backend service to handle the request by path matching.

## Step 8: Request Transformation and Backend Service Communication
<img width="362" alt="image" src="https://github.com/user-attachments/assets/4b3edeac-9a4a-422f-b160-646713012e4b" />

- The API gateway transforms the request into the appropriate protocol and sends it to the backend service (e.g., using gRPC).
- When the response comes back from the backend service, the API gateway transforms the response back into the public-facing protocol and returns the response to the client.

---
A proper API gateway also  provides other critical services.
For example, an API gateway should track errors  
and provide circuit-breaking functionality  to protect the services from overloading.
An API gateway should also  provide logging, monitoring,  
and analytics services for  operational observability.
An API gateway is a critical  piece of the infrastructure.
It should be deployed to multiple  regions to improve availability.
For many cloud provider offerings, the API gateway  is deployed across the world close to the clients.
If you like our videos, you may like our  weekly system design newsletter as well.
It covers topics and trends  in large-scale system designs.
![image](https://github.com/user-attachments/assets/cae75104-ee3f-4ef0-8729-fb628e0bb61e)


