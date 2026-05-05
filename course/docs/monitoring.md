**📊 Monitoring --- "Is the system healthy?"**

If logging tells you what happened, monitoring tells you whether your
system is *okay right now*.

Instead of individual events, monitoring focuses on **metrics over
time**:

- CPU usage

- Memory consumption

- Request rate

- Error rate

- Latency (p50, p95, p99)

These metrics are typically collected and visualized using tools like
Prometheus and Grafana.

------------------------------------------------------------------------

**What Monitoring Does Well**

Monitoring is your **early warning system**.

It helps you:

- Detect incidents quickly

- Set alerts (e.g., "p95 latency \> 500 ms")

- See trends over time

- Understand system load and capacity

For example, a dashboard might show:

- Latency gradually increasing

- Error rate spiking

- Traffic doubling

This is incredibly valuable---it tells you *something is wrong* before
users start complaining.

------------------------------------------------------------------------

**Where Monitoring Falls Short**

The problem is what happens next.

You see:

- CPU = 85%

- Latency = 2 seconds

- Error rate increasing

Now what?

Monitoring doesn't tell you:

- Which endpoint is causing the issue

- Which dependency is slow

- Whether the problem is in your code or elsewhere

- Why it only happens under load

You're still missing the context.

------------------------------------------------------------------------

**A Common Trap**

Teams often invest heavily in dashboards:

- Dozens of graphs

- Multiple environments

- Detailed infrastructure metrics

But when an incident happens, they still ask:

*"Where do we even start?"*

That's because dashboards show **aggregated data**.

They smooth out the details:

- Averages hide spikes

- Global metrics hide problematic endpoints

- System-wide views hide request-level behavior

**Example**

Imagine this situation:

- p95 latency jumps to 2 seconds

- CPU is stable

- Memory is stable

Monitoring tells you:

- The system is slow.

But it doesn't tell you:

- Is it the database?

- A specific API endpoint?

- A downstream service?

- A single slow query affecting only some requests?

You're still guessing---just with better graphs.

------------------------------------------------------------------------

**The Role of Monitoring**

Despite its limitations, monitoring is essential.

It answers:

- **When** something went wrong

- **How bad** it is

- **Whether it's getting worse**

But it stops short of explaining *why*.

------------------------------------------------------------------------

**Takeaway**

Monitoring is necessary---but not sufficient.

It tells you **that** something is broken, but not **what** or **why**.

To move from detection to understanding, you need one more
piece---something that connects the dots across your system.