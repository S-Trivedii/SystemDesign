## What is a Client and Server?

- **Client:** A device or program that requests services or resources from another device (the server).  
  **Example:** Your web browser sends a request to load a webpage.

- **Server:** A device or program that provides services or resources to clients.  
  **Example:** A web server hosting a website responds with the webpage data.

---

## What is a Database?

A **database** is an organized collection of data that can be easily accessed, managed, and updated. It stores information like user data, product info, or any other structured data.

**Example:** An online store database contains tables for products, users, orders, etc.

---

## What is Vertical Scaling and Horizontal Scaling?

- **Vertical Scaling:** Increasing the capacity of a single server by adding more CPU, RAM, or storage. But hardware has its limit.  
  **Example:** Upgrading a server from 8GB RAM to 32GB RAM.

- **Horizontal Scaling:** Adding more servers to handle increased load by distributing the workload.  
  **Example:** Adding three more web servers behind a load balancer to handle more visitors.

### When system started to get overwhelmed with hugh number of users, vertical scaling and horizontal scaling comes into picture.

---

## What is a Load Balancer?

A **load balancer** distributes incoming network or application traffic across multiple servers to ensure no single server is overwhelmed. It sits between client and server.

**Example:** If you have 5 web servers, the load balancer sends user requests evenly among them to keep response times fast.

---

## What is Database Sharding?

**Database sharding** is splitting a large database into smaller, faster, more manageable pieces called shards (database). Big system like youtube, twitter uses sharding. It increases performace (fast queries), scalibility.

**Example:** User data might be split by region: users from North America are in one shard, users from Europe in another.

---

## What is Database Replication?

**Database replication** means copying database data across multiple servers to improve availability.

**Example:** A primary database handles writes, and replicas sync data for read queries, so reads are faster and fault-tolerant.

---

## What is Cache?

**Cache** is temporary storage that holds copies of frequently accessed data to speed up retrieval.

**Example:** A website caches user profile info in memory so it doesn’t query the database every time.

Let’s say a user visits your site and views a product page:

1. First time → data is fetched from the database and stored in cache.
2. Next time → same data is returned directly from cache, much faster.

### Common Cache Tools

- In memory cache - Fastest, used for temporary data
- Browser cache - stores static files (images, CSS, etc.)
- CDN cache - Stores content geographically closer to users

### Bonus

In React apps, you might cache API responses using tools like:

- React Query
- SWR

---

## What is Object Storage?

**Object storage** stores data as objects with metadata and unique IDs, good for unstructured data. It is not good for data which is frequently updated. Generally, we store static data (data which do not change like HTML files, images, intro videos etc)

**Example:** Storing photos and videos in Amazon S3, where each file is an object accessed via a unique URL.

---

## What is CDN and How is it Useful?

A **Content Delivery Network (CDN)** is a network of servers worldwide that deliver content from the closest server to the user, improving speed and reliability.

**Example:** When you load a popular website, images and scripts are served from a CDN server near your location for faster load times. CDN uses cacheing. Clouflare, Amzon CloudFront, Akamai are some popular CDN.

---

## How is Netflix Streaming So Fast? Does it Have Anything to Do with CDN?

Yes! Netflix uses a its own CDN called **Open Connect** which caches videos close to users inside ISPs.

**Example:** When you watch a Netflix movie, the video streams from a nearby CDN server, reducing buffering.

---

## Monolith vs Microservices

| Aspect           | Monolith                              | Microservices                       |
| ---------------- | ------------------------------------- | ----------------------------------- |
| Structure        | Single unified codebase               | Multiple small independent services |
| Deployment       | One big deploy                        | Multiple smaller deploys            |
| Scalability      | Scale entire app                      | Scale individual services           |
| Team size        | Small to medium                       | Larger teams or multiple teams      |
| Tech flexibility | Usually one tech stack                | Different tech per service possible |
| Complexity       | Simpler initially                     | Complex distributed system          |
| Fault isolation  | Failure in one part affects whole app | Failure isolated to service         |

**Example:**

- **Monolith:** A traditional web app where user login, product catalog, and checkout are all in one codebase.
- **Microservices:** Separate services for user auth, product catalog, payments, each deployed independently.

---

## What is a Message Queue and Why is it Needed? (With Example)

A **message queue** lets different parts of a system communicate asynchronously by sending messages to a queue, processed later by consumers.

### Why needed?

- Asynchronous processing
- Decoupling services
- Load leveling
- Reliability and retries

### Example:

In an e-commerce app, when a user places an order, the order service puts an "order placed" message in a queue. The payment and shipping services consume this queue independently. If payment service is busy, the message waits safely until processed.

### Popular message queue

- RabbitMQ

- Apache Kafka

- Amazon SQS

- Redis Streams

---

## API Gateway

An API Gateway is a server that acts as a single entry point (or "gatekeeper") for all client requests to a system’s backend services or microservices.
