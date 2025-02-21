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
- The request is typically HTTP-based. It could be REST, GraphQL, or some other higher-level abstractions.

## Step 2: API Gateway Validates the HTTP Request
- The API gateway checks the validity of the incoming request.

## Step 3: API Gateway Checks Caller’s IP and HTTP Headers
- The API gateway checks the caller’s IP address and other HTTP headers against its allow-list and deny-list.
- It could also perform basic rate limit checks against attributes such as IP address and HTTP headers.
- For example, it could reject requests from an IP address exceeding a certain rate.

## Step 4: Request Passed to Identity Provider for Authentication and Authorization
- The API gateway passes the request to an identity provider for authentication and authorization.
- This is a complex process and may include checking user credentials, tokens, etc.
- The API gateway receives an authenticated session back from the provider with the scope of what the request is allowed to do.

## Step 5: Higher-Level Rate Limit Check
- A higher-level rate limit check is applied to the authenticated session.
- If the request exceeds the limit, it is rejected at this point.

## Step 6 and 7: Service Discovery and Path Matching
- With the help of a service discovery component, the API gateway locates the appropriate backend service to handle the request by path matching.

## Step 8: Request Transformation and Backend Service Communication
- The API gateway transforms the request into the appropriate protocol and sends it to the backend service (e.g., using gRPC).
- When the response comes back from the backend service, the API gateway transforms the response back into the public-facing protocol and returns the response to the client.

---

