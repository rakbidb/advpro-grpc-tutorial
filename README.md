# Reflection

## 1. What are the key differences between unary, server streaming, and bidirectional streaming RPC methods, and when is each most appropriate?

- **Unary RPC**: The client sends one request and receives one response. Ideal for simple interactions with minimal data exchange.
- **Server Streaming RPC**: The client sends a single request and receives a stream of responses. Best suited for scenarios requiring multiple pieces of data from the server.
- **Bidirectional Streaming RPC**: Both client and server can send and receive a stream of messages concurrently. Suitable for interactive use cases, such as real-time communication.

## 2. What are the security considerations when implementing a gRPC service in Rust, especially for authentication, authorization, and data encryption?

- **Authentication**: gRPC supports SSL/TLS, OAuth2, and token-based methods. Rust servers can use mutual TLS (mTLS) for identity verification or OAuth2/token exchanges for authentication.
- **Authorization**: Implement access control using interceptors or middleware. Apply role-based (RBAC) or attribute-based (ABAC) policies and ensure consistency across endpoints.
- **Data Encryption**: gRPC uses HTTP/2, which supports SSL/TLS. In Rust, libraries like `rustls` or `native-tls` can secure communications. For added security, apply application-level encryption for sensitive data and follow best practices for key management.

## 3. What challenges may arise in handling bidirectional streaming in Rust gRPC, especially for applications like chat systems?

Synchronizing state and ensuring correct message ordering are major challenges. Real-time delivery and resilience to network failures or disconnections require robust error handling and retry logic to maintain a seamless user experience.

## 4. What are the pros and cons of using `tokio_stream::wrappers::ReceiverStream` for streaming responses in Rust gRPC?

- **Pros**: Offers simple integration with Tokio, enables easy conversion of channels into streams, and simplifies async stream handling.
- **Cons**: Tightly coupled with the Tokio runtime, limiting flexibility if switching to another async runtime is required.

## 5. How can Rust gRPC code be structured to support reuse and modularity for long-term maintainability?

Use modules and traits to encapsulate logic, and separate business logic from gRPC-specific code. This separation improves testability, promotes code reuse, and allows for easier implementation changes.

## 6. What additional considerations are needed for more complex logic in the `MyPaymentService` implementation?

Complex payment processing requires thorough validations (e.g., checking for sufficient funds or negative values), along with detailed error handling to manage various edge cases reliably.

## 7. How does adopting gRPC affect the architecture of distributed systems, particularly regarding interoperability?

gRPC improves inter-service communication through efficient and scalable design. Protocol Buffers enable smaller, faster messages compared to REST/JSON, enhancing performance and cross-platform interoperability.

## 8. What are the benefits and drawbacks of HTTP/2 (used by gRPC) versus HTTP/1.1 or WebSockets for REST APIs?

HTTP/2 offers multiplexing, header compression, and lower latency. In contrast, HTTP/1.1 with WebSockets may be simpler and more widely supported but lacks the efficiency gains of HTTP/2, especially for concurrent small requests.

## 9. How does the REST request-response model differ from gRPC's bidirectional streaming in terms of real-time responsiveness?

REST follows a single-request, single-response model, which can introduce latency in real-time scenarios. gRPC’s bidirectional streaming enables continuous, real-time data flow in both directions over a single connection, enhancing responsiveness.

## 10. What are the implications of gRPC's schema-based approach (Protocol Buffers) compared to REST's schema-less JSON?

Protocol Buffers enforce strict schemas, ensuring type safety and data validation, which reduces communication errors. JSON offers flexibility and ease of integration, allowing for rapid development and adaptability, but may be less consistent and efficient.