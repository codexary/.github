English · [简体中文](README.zh-CN.md)

<p>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="card-en-dark.svg">
  <img src="card-en-light.svg" width="100%" alt="Stubline: browse events, sign in, hold seats, pay once, get the e-ticket.">
</picture>
</p>

Stubline is Elsworne's event-ticketing product and the case for the book on distributed systems. Buyers browse events and seats, sign in, hold seats, pay once and download an e-ticket; the team has to keep that working when a sale opens and thousands of buyers arrive at once.

- **Backend.** Starts as a single service on one network connection and grows into separate ticketing, inventory and notification services, with a database, messaging, object storage for e-tickets, TLS and signed tokens between services, tracing, and rehearsed failures.
- **Frontend.** The buyer's site, from event listings to the downloaded ticket, including sign-in and paying without being charged twice.
- **Spikes.** Short experiments the team ran before committing to a design, each on one question.

## Try it

- [Open the backend in GitHub Codespaces](https://codespaces.new/codexary/stubline-backend). Usage counts against your own GitHub quota.
- [Try the buyer site in the browser](https://codexary.github.io/stubline-web/). It uses simulated data and needs no backend.

## Repositories

| Repository | Type | Description |
| --- | --- | --- |
| [stubline-backend](https://github.com/codexary/stubline-backend) | Backend | Stubline event-ticketing backend: ticketing API, inventory (gRPC), notifications (Kafka outbox), e-tickets on S3, TLS/JWT, OpenTelemetry and failure drills. Java 21. |
| [stubline-web](https://github.com/codexary/stubline-web) | Frontend | Stubline buyer site: browse events and seats, sign in with OAuth 2.0 + PKCE, reserve, pay once with an idempotency key, download the e-ticket. React + TypeScript. |
| [stubline-spike-dns-query](https://github.com/codexary/stubline-spike-dns-query) | Spike | Build and decode DNS query messages over UDP by hand (A, CNAME, NXDOMAIN, timeouts). |
| [stubline-spike-resp-server](https://github.com/codexary/stubline-spike-resp-server) | Spike | A minimal RESP2 server that the real redis-cli can talk to, to learn the Redis wire protocol. |
| [stubline-spike-health-checker](https://github.com/codexary/stubline-spike-health-checker) | Spike | Concurrent HTTP health checks with platform threads, a bounded pool and virtual threads. |
| [stubline-spike-rate-limiter](https://github.com/codexary/stubline-spike-rate-limiter) | Spike | A token-bucket rate limiter and how its correctness depends on the concurrency strategy. |
| [stubline-spike-fault-injection](https://github.com/codexary/stubline-spike-fault-injection) | Spike | Inject latency, bandwidth limits, timeouts and resets with Toxiproxy and watch a client's deadlines. |
| [stubline-spike-cgroup-memory](https://github.com/codexary/stubline-spike-cgroup-memory) | Spike | JVM heap limits versus container cgroup memory limits, and what an OOM kill looks like. |
| [stubline-spike-spring-boot](https://github.com/codexary/stubline-spike-spring-boot) | Spike | The ticketing routes in Spring Boot, to see what the framework hides and what it cannot decide. |
| [stubline-spike-webhook-receiver](https://github.com/codexary/stubline-spike-webhook-receiver) | Spike | Receive payment webhooks safely: HMAC signatures, replay window and duplicate events. |
| [stubline-spike-rpc-styles](https://github.com/codexary/stubline-spike-rpc-styles) | Spike | The same seat-hold service over Java RMI, gRPC and REST. |
| [stubline-spike-rabbitmq-tasks](https://github.com/codexary/stubline-spike-rabbitmq-tasks) | Spike | Ticket-rendering tasks on RabbitMQ work queues with acknowledgements and a dead-letter queue. |
| [stubline-spike-redis-pubsub](https://github.com/codexary/stubline-spike-redis-pubsub) | Spike | Redis pub/sub versus Redis Streams for seat updates: late and slow subscribers, replay. |
| [stubline-spike-nfs-cache](https://github.com/codexary/stubline-spike-nfs-cache) | Spike | NFSv3 and NFSv4 client caching, close-to-open consistency and write policies between two clients. |
| [stubline-spike-dns-cache](https://github.com/codexary/stubline-spike-dns-cache) | Spike | Where DNS answers are cached (resolver, JVM, gRPC) and how long a stale address survives. |
| [stubline-spike-keycloak-oauth](https://github.com/codexary/stubline-spike-keycloak-oauth) | Spike | Keycloak with Spring Security: authorization code + PKCE for buyers, client credentials for services. |
| [stubline-spike-kind-failover](https://github.com/codexary/stubline-spike-kind-failover) | Spike | Lose a whole Kubernetes node in kind, compare with a planned drain, and count failed requests. |

> Elsworne, Stubline and the team are fictional. The book and code were written with the help of AI tools; every output quoted in the book comes from actually running the code.
