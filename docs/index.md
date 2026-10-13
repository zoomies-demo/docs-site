# Zoomies Demo Docs

The documentation for the demo organisation's two projects:

* **[storefront](storefront.md)**, a small shopping cart library.
* **[payments-api](payments-api.md)**, a charges service with safe retries.

These repositories exist for one reason. They are what the public demo of
[Zoomies](https://zoomies.sh) runs its jobs on. Every job in the demo's web UI
was started by a workflow in one of them, on a runner that Zoomies created for
that job and destroyed when it finished.

1. A demo repository's scheduled workflow starts, and GitHub queues its jobs.
2. Zoomies sees the queued job and starts a runner for it.
3. The job runs on that runner.
4. The runner is destroyed when the job finishes.
