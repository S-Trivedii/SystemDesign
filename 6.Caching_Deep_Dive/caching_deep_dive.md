# ⚡ Caching Strategies

- Caching is a technique that is used to speed up the data retrieval ⚡
- By storing frequently accessed data in a fast access cache 🧠

## 📖 There are two types of **Read Caching Strategies**

1. 🧩 Cache Aside Strategy
2. 🔁 Read Through Strategy

---

## 🧩 Cache Aside Strategy

- Server would first check in the cache to see if the data is already available 🔍
- If the data is not found, AKA a cache miss ❌
- Then the server would retrieve this data from the database 💾
- It would store in the cache so that it will be available for any other future requests 📥

---

## 🔁 Read Through Strategy

- The cache itself would be responsible for fetching the data if it's not already present ⚙️
- Cache will first check if the data is available 🔎
- If not, the cache itself would fetch that data from the database and save it in the cache for future requests 💡

> In both the strategy, **the goal is to minimize expensive database reads by using the cache for frequently requested data** 💰

---

## ✍️ There are three types of **Write Caching Strategies**

1. 💤 Write Aside Strategy
2. 🖊️ Write Through Strategy
3. ⏳ Write Behind Strategy

---

## 💤 Write Aside Strategy (or lazy write)

- When the application **writes (updates or insert)** data, it first **writes the data to the database** 💽
- Then it **invalidates** or **updates the cache** during the read process 🔁  
  _Updation or invalidation don't happen during the write phase_ ⚠️

---

## 🖊️ Write Through Strategy

- Write-through is a caching strategy where every write operation (insert/update) is done to both:

1. The cache 🗃️
2. The database 💾

at the same time, in a synchronous manner ⏱️

```plaintext
1. Application writes data to the cache 🗃️
2. Cache writes the same data to the database 💾
```

---

## ⏳ Write Behind Strategy

- Write-behind is a caching strategy where the application writes data only to the cache, and the cache is responsible for asynchronously writing that data to the database later

```plaintext
1. Application writes data to the **cache only**
2. Cache queues the write and pushes it to the **database asynchronously** (after a delay or in batches)
```

```plaintext
App → Cache (write immediately)
      ↓
   Cache → DB (writes after a delay or in background)
```

---
