# Multithreaded Proxy Server 🧩

A C‑language project that implements a high-performance, multithreaded proxy server with optional caching, designed as part of systems programming coursework.

## 🚀 Features

- **Multi-threaded architecture**: Handles multiple simultaneous client connections efficiently using POSIX threads.
- **LRU cache support**: (Optional) Implements a Least‑Recently‑Used cache to store and serve frequently requested resources faster.
- **Concurrent-safe handling**: Manages shared resources with mutexes and semaphores to avoid race conditions.
- **HTTP GET support**: Processes only `GET` requests—it’s a focused and educational proxy server, ideal for learning purposes.

## 🧱 Tech Stack

- **Language**: C
- **Concurrency primitives**: `pthread`, `sem_t`, `pthread_mutex_t`
- **Networking**: BSD sockets (`<sys/socket.h>`, etc.)
- **Build system**: `Makefile` for compilation and execution

## 🧭 Usage

1. **Clone this repository**  
   ```bash
   git clone https://github.com/Anirudh-N-15/Multithreaded-Proxy-Server.git
   cd Multithreaded-Proxy-Server


2. **make all**

3. **./proxy <port no.>**

   `Open http://localhost:port/https://www.cs.princeton.edu/`

# Note:
- This code can only be run in Linux Machine. Please disable your browser cache or run in incognito mode.

##### Limitations ​
- If a URL opens multiple clients itself, then our cache will store each client’s response as a separate element in the linked list.
- During retrieval from the cache, only a chunk of response will be sent and the website will not open.
- Fixed size of cache element, so big websites may not be stored in cache.

##### OS Component Used ​
- Threading
- Locks 
- Semaphore
- Cache (LRU algorithm is used in it)


##### How did we implement Multi-threading?
- Used Semaphore instead of Condition Variables and pthread_join() and pthread_exit() function. 
- pthread_join() requires us to pass the thread id of the the thread to wait for. 
- Semaphore’s sem_wait() and sem_post() doesn’t need any parameter. So it is a better option.

##### Motivation/Need of Project
- To Understand → 
  - The working of requests from our local computer to the server.
  - The handling of multiple client requests from various clients.
  - Locking procedure for concurrency.
  - The concept of cache and its different functions that might be used by browsers.
- Proxy Server do → 
  - It speeds up the process and reduces the traffic on the server side.
  - It can be used to restrict user from accessing specific websites.
  - A good proxy will change the IP such that the server wouldn’t know about the client who sent the request.
  - Changes can be made in Proxy to encrypt the requests, to stop anyone accessing the request illegally from your client.
   
