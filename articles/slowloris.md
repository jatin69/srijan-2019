# The Slowloris Attack

---

| Question   | Answer                                                                 |
| ---------- | ---------------------------------------------------------------------- |
| Writer     | Abhinav Kumar - MSc I year                                             |
| Editor     | Swati Gautam - MSc I year                                              |
| Status     | Reviewed.                                                              |
| Plagiarism | None. 100% unique. [Report Link](./plag-reports/plag-slowloris-v1.pdf) |
| Content    | HTTP request - Slowloris - conclusion                                  |
| Verdict    | Okay Candidate.                                                        |

---
> Slow loris are very slow animals, so slow that you might believe you were watching a video in slow motion.

Let's start with an analogy. Imagine yourself standing in a queue at the checkout of a shop. The person at the checkout can only handle one customer at a time. As casually as you're waiting for your turn to come, you see people cutting in line before you for no reason other than to disrupt the queue being served. They aren't even legitimate customers, they just don't like you. Refuting you service is their only aim.
This is known as *Denial of Service(DoS)*

In the world of computer science, DoS attack is a cyber-attack in which the offender renders a network or a machine inaccessible to legitimate requests from a client usually by flooding the server with overwhelming traffic.

This article talks of a DoS attack mechanism, famously used by protestors during the 2009 Iranian presidential elections to bring down government-owned websites.

When you open up your web browser and enter a URL, you are basically communicating with a computer(called the server) and making a few GET requests over HTTP.
For illustration,

> get me index.html

The server on receiving this, responds(send the specific file). Thus, marking the end of the conversation. This simple mechanism is what an attacker takes advantage of in the Slowloris attack. Any connection made with the server is allowed to remain idle only for a specific amount of time. The server maintains a connection-timeout header to contain the same.

Slowloris establishes a connection, requests something from the server and then goes to sleep. The moment the connection exceeds its time-limit and the server is about to break it, the Slowloris attacker sends something more. It could be anything, even a partial request. Its only aim is to tell the server that the connection is still alive. The socket through which the server and the attacker were communicating ends up withheld. Imagine the same scenario with hundreds of sockets! The server will keep on serving these time-consuming requests.

The affected server will have its connection pool exhausted. As a consequence, it won't be able to serve a legitimate request. This is what makes Slowloris a **denial of service(DoS)** attack. The beauty of this attack is that it only occupies a fraction of bandwidth on the attacker's end. Also, compared to other DoS attacks, Slowloris is very hard to detect because there is nothing wrong with the requests it sends. The server just assumes that the requesters have a really bad internet connection which is a fairly normal occurrence. Apache web is more prone to this attack because it makes a new thread for every new request. Apache has a limit on the number of concurrent connections it can handle.

The communication will work perfectly fine if requests come and go. Precisely what Slowloris prevents.
