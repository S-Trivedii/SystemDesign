# 1. 🔗 What is an API?

## 💡 Definition

**API** stands for **Application Programming Interface**.  
It is a **set of rules and protocols** that allows **two software applications** to **communicate** with each other.

---

## 🧩 Real-World Analogy

Imagine a **restaurant**:

- You (the client) ask the waiter (API) for food.
- The waiter takes your request to the kitchen (server).
- The kitchen prepares the food and gives it to the waiter.
- The waiter brings it back to you.

> 👉 The **waiter = API** — it connects the **client** and the **server**.

---

## ⚙️ How an API Works

1. **Client sends a request** (usually via HTTP).
2. The **API processes** the request and forwards it to the appropriate service.
3. The service sends back the response through the API.
4. The client receives the response (data, confirmation, etc).

---

## Three ways to design and implement APIs

1. REST
2. GraphQL
3. gRPC

---

# 2. 🔍 What is GraphQL?

## 💡 Definition

**GraphQL** is a **query language** for APIs and a **runtime** for executing those queries.  
It allows **clients to request exactly the data they need** — nothing more, nothing less.

It was developed by **Facebook** and is now open-source.

---

## ⚙️ Traditional REST vs GraphQL

### REST API:

- Fixed endpoints (e.g., `/users`, `/users/1/posts`)
- Over-fetching or under-fetching data is common

### GraphQL:

- Single endpoint (usually `/graphql`)
- Client defines the **structure of the response**

---

## 🧩 Real-World Analogy

> Imagine ordering food at a restaurant:

- **REST API**: You get a full combo meal every time, even if you only want fries.
- **GraphQL**: You can **customize your order** — just fries and a drink.

---

# 3. ⚙️ What is gRPC?

## 💡 Definition

**gRPC** stands for **Google Remote Procedure Call**.  
It is a **high-performance, open-source framework** developed by **Google** that allows services to communicate with each other **directly** using **function calls**, even if they are on different machines.

---

## 🔗 Basic Idea

Instead of sending HTTP requests like REST, gRPC lets you call a function on another server as if it were local.

> gRPC = "Call a function remotely, like it's in your own code"

---

## 📦 Key Components

| Component                       | Description                                                                 |
| ------------------------------- | --------------------------------------------------------------------------- |
| **Protocol Buffers (protobuf)** | Language for defining data structure and service contracts. Compact & fast. |
| **Stub**                        | Auto-generated client code from `.proto` file to call remote functions      |
| **Server**                      | Implements the service defined in `.proto` file                             |
| **Client**                      | Uses the stub to call methods on the server                                 |

---

# 4. 📩 What is a Message Queue?

## 💡 Definition

A **Message Queue** is a **communication system** used for **sending and receiving messages between distributed systems or services**.

It acts like a **temporary storage** where messages wait until the receiving service is ready to process them.

---

## 🧩 Real-Life Analogy

> Imagine a **queue at a bank**:

- Customers (messages) wait in line.
- The teller (consumer) serves one at a time.
- If the teller is busy, customers wait — no one gets lost.

---

## ⚙️ How It Works

### Components:

1. **Producer** – sends messages to the queue.
2. **Queue (Broker)** – holds the messages.
3. **Consumer** – receives and processes messages from the queue.

### Flow:

[Producer] ➡️ [Message Queue] ➡️ [Consumer]

---

## 📦 Example Use Case

- **Order Processing System**:
  - User places an order (producer).
  - Order details go into the queue.
  - Backend service (consumer) processes orders from the queue one by one.

---

## 🔄 Benefits

| Benefit             | Description                                               |
| ------------------- | --------------------------------------------------------- |
| ⏳ **Decoupling**   | Producer and consumer don’t need to work at the same time |
| ⚙️ **Scalability**  | Consumers can be scaled based on load                     |
| 📬 **Reliability**  | Messages are not lost even if the consumer is down        |
| 🚀 **Asynchronous** | Improves performance by not blocking producers            |

---

## 🛠️ Popular Message Queues

| Tool             | Description                                    |
| ---------------- | ---------------------------------------------- |
| **RabbitMQ**     | Lightweight, supports complex routing          |
| **Apache Kafka** | Great for large-scale, high-throughput systems |
| **Amazon SQS**   | Fully managed message queue by AWS             |
| **Redis**        | Lightweight in-memory queue option             |

---

## 🧠 Summary

> A **Message Queue** helps different parts of an application communicate **asynchronously and reliably**, making the system **scalable**, **resilient**, and **fault-tolerant**.

---

# 5. 🌐 What is a REST API?

## 💡 Definition

**REST API** stands for **Representational State Transfer Application Programming Interface**.  
It is a **standard way for two systems to communicate** over the web using **HTTP** methods.

---

## 📦 What is an API?

> An **API** (Application Programming Interface) is a set of rules that lets one software talk to another.

---

## ⚙️ What Makes an API "RESTful"?

To be RESTful, an API must follow these **6 key principles**:

1. **Stateless** – No session/state is stored on the server.
2. **Client-Server** – Frontend (client) and backend (server) are separate.
3. **Uniform Interface** – Common structure (URLs, methods).
4. **Cacheable** – Responses can be cached to improve performance.
5. **Layered System** – Architecture with multiple layers (e.g., middleware, databases).
6. **Code on Demand** _(optional)_ – Server can send executable code (rarely used).

---

## 🧩 Real-World Analogy

> Think of a REST API like a **waiter** in a restaurant:

- You (client) ask for food (data).
- The waiter (API) brings your food (response) from the kitchen (server).

---

## 📮 Common HTTP Methods

| Method | Action          | Example URL |
| ------ | --------------- | ----------- |
| GET    | Read data       | `/users`    |
| POST   | Create new data | `/users`    |
| PUT    | Update existing | `/users/1`  |
| DELETE | Delete data     | `/users/1`  |

---

## 🧾 Example REST API

### Client Request:

```http
GET /users/1

```

---

# How REST is different than GraphQL?

## REST API approach

REST uses multiple endpoints, and the data returned is often fixed.

### 💡 What the frontend needs:

- User's name and email

- List of the user's orders (only order ID and product name)

---

### REST Calls:

1. GET /users/123
   → Returns:

```bash
{
  "id": "123",
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "1234567890",
  "address": "New York"
}
```

👉 **Problem:** More data than needed (e.g., phone, address).

2. GET /users/123/orders
   → Returns:

```json
[
  {
    "orderId": "001",
    "productName": "Laptop",
    "price": 1000,
    "shippingDetails": { ... }
  },
  {
    "orderId": "002",
    "productName": "Mouse",
    "price": 20,
    "shippingDetails": { ... }
  }
]
```

👉 **Problem:** Again, more data than needed (e.g., price, shipping details).

📌 You make multiple API calls and often get too much data.

---

## 🔹 GraphQL Approach

GraphQL uses a single endpoint, and you ask exactly for what you need.

### GraphQL Query:

```graphql
{
  user(id: "123") {
    name
    email
    orders {
      orderId
      productName
    }
  }
}
```

-> Response

```json
{
  "data": {
    "user": {
      "name": "John Doe",
      "email": "john@example.com",
      "orders": [
        {
          "orderId": "001",
          "productName": "Laptop"
        },
        {
          "orderId": "002",
          "productName": "Mouse"
        }
      ]
    }
  }
}
```

✅ **Only one request**
✅ **Only the required fields are fetched**
✅ **More efficient and cleaner**
