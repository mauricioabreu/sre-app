# SRE Hands On

This tutorials is a hands on to [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering).

## Performance

Observing how a system performs is not something new, but it changed drastically over the years.

I remember the time we had no idea if a system was running under good conditions. How did we know something was failing? We didn't. Customers used to be our alert system. If everything was silent, it was a sign that everything was working fine. Otherwise, customers would be flooding the project manager's inbox. At that time, we had scripts reading the last lines of log files looking for words like "ERROR", "Exception" and so on.

Nowadays, we have plenty of tools and strategies to parse, collect and use all the information we can extract from systems. This wide and diverse range of tools may confuse even experiencied developers. What tools do we need? Which metrics we must collect? Will these numbers show how buggy is my code?

If you are working in a healthy environment, you should not worry whether these numbers will impact your reasoning about your team's code quality. Measuring should serve for one thing only: understanding systems. And when I say _understand_, I'm talking about awaraness. We should not need to keep eyes on log parsers, charts or email inbox to check if all systems are up and running. Our job, as developers, is to automate these processes.

### Availability

**Availability** is the word used to define whether a system is able to complete a request from a client. We use the word _client_ because we don't care whether the request comes from humans or tools.

If a GET request to `/todos` route works, it means the route works and the requests completes. Does it mean that the application is available?

Availability if often measured by using the following formula:

$sucessful / (successful + failed)$

Let's check some examples:

* Our app receives *1000* requests in the past minute.
* 100 out of 1000 requests fail
* 900 / (900 + 100) = 0.9
* Our app has **90% of availability**

### Latency

**Latency** measures how long a request takes to complete. How long does it take to process a job.

We use latency to measure the overall user experience.

Slow responses will force our users to leave websites. And we don't want it. Availability is important. We wish our applications responding **HTTP 200 OK** but a good status can't come with a high latency. We don't want our applications responding fast **HTTP 5xx** errors in the same way we don't want **HTTP 2xx** taking 10 second to complete.
