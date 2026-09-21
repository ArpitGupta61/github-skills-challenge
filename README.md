# GitHub Challenge

<img src="https://octodex.github.com/images/Professortocat_v2.png" align="right" height="200px" />

Hey there!

Your challenge is ready.
Follow the instructions provided for this challenge and complete the required tasks in this repository.

Make sure your work is committed and pushed to your repository before submission.

Good luck!

## AIOps Assessment

This project monitors a `payment-service` that processes payment requests.

The operational problem is that some requests become slow and fail because of payment and database timeouts.

AIOps checks the service metrics and logs to find unusual behaviour and create anomaly events.

The metric fields are:

- `response_time_ms`
- `cpu_percent`
- `memory_percent`

The log fields are:

- `log_level`
- `message`

The normal records are from `10:00–10:04` and `10:07–10:09`.

Two anomalies were detected:

- `10:05`: 610 ms response time and an `ERROR` payment timeout.
- `10:06`: 640 ms response time, 94% CPU, 91% memory, and an `ERROR` database timeout.

The detector was updated to recognise `ERROR` logs, and the pipeline was updated so the producer and consumer use the same topic. The pipeline processed 10 records, detected 2 anomalies, and consumed 2 events.

One limitation is that the detector uses fixed thresholds and may not adapt to changing traffic levels.
---

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

