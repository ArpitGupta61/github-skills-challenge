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

## What I completed

- Looked through the service data and the main AIOps files.
- Checked the normal records and found the two unusual records.
- Fixed the detector so it also notices `ERROR` logs.
- Fixed the event flow so the producer and consumer use the same topic.
- Ran the pipeline: 10 records were checked, 2 anomalies were found, and 2 events were received.

The event flow is: detector -> event -> producer -> topic -> consumer -> AIOps result.

No normal records were flagged, and no expected anomalies were missed.

## Task 5: Workflow Fixes

I found two problems in the provided workflow.

First, the anomaly detector only checked for `WARNING` logs, but the data contained `ERROR` logs. I updated the detector to recognise both levels.

Second, the producer and consumer were using different topic objects, so the consumer received no events. I connected both components to the same anomaly topic.

After the fixes, the pipeline processed 10 records, detected 2 anomalies, and consumed 2 events successfully.
---

## Task 6: End-to-End Pipeline

I ran the complete AIOps workflow from the operational data through anomaly detection, event creation, producer, topic, consumer, and final output.

The pipeline processed 10 records, detected 2 anomalies, and consumed 2 events. The final output showed the payment timeout at `10:05` and the database timeout at `10:06`, including the reasons why they were flagged.

## How to Reproduce

1. Open the repository in the Codespace.
2. From the project folder, run:

```bash
PYTHONPATH=src python aiops_pipeline.py

## Task 8: Validation

The provided tests passed with 8 tests passing. The full pipeline also completed successfully. It processed 10 records, detected 2 anomalies, and consumed 2 events.

&copy; 2025 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

