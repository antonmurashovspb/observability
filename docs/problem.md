<iframe src="https://epam-my.sharepoint.com/personal/anton_murashov_epam_com/_layouts/15/embed.aspx?UniqueId=9e210307-fdf5-4ef7-b57e-84d81a706a96&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create" width="640" height="360" frameborder="0" scrolling="no" allowfullscreen title="Logging vs Monitoring vs Observability - What Most Developers Get Wrong - Problem.mp4"></iframe>
<br>
<br>
**🚨 The Problem**

Everything looked fine---until it didn't.

Our service was handling around 200 requests per second without any
noticeable issues. Latency stayed within 120--150 ms, CPU usage was
stable, and error rates were close to zero. From the outside, the system
looked healthy.

Then traffic increased.

At around 800 requests per second, things started to fall apart:

- p95 latency jumped to **2--3 seconds**

- Error rate climbed to **\~8%**

- Timeouts began cascading across dependent services

- CPU usage spiked unpredictably

What made it worse: nothing obvious had changed. No recent deployments,
no infrastructure changes, no clear regression point.

So, we did what most teams do first:

- Checked logs

- Looked at dashboards

- Tried to reproduce the issue locally

But the signals didn't line up.

Logs showed scattered warnings, but nothing clearly tied to the latency
spike. Metrics indicated that something was wrong---but not *what* or
*where*. Different services looked healthy in isolation, yet the system
as a whole was clearly struggling.

At this point, the problem wasn't just performance.

The real issue was lack of visibility.

We couldn't answer basic questions:

- Which endpoint is actually slow?

- Is the bottleneck in our service or a dependency?

- Are we CPU-bound, IO-bound, or waiting on something external?

- Why does latency spike only under load?

Without clear answers, every step forward was a guess.

And that's the trap many systems fall into:

> *When performance issues appear, the hardest part isn't fixing them
> --- it's understanding them.*

That's where observability becomes critical.