# The Phantom Login

- **Category:** Forensics
- **Flag:** `spooky{the_ghost_left_a_trace}`

## Solution

### 1. Log File Analysis
Inspected the provided `.log` file and identified an anomalous HTTP GET request near the end of the log entries:

```log
2026-10-31T03:19:08Z src=203.0.113.77 user=evelyn.graves "GET /archives/export?note=c3Bvb2t5e3RoZV9naG9zdF9sZWZ0X2FfdHJhY2V9 HTTP/1.1" status=200
```

### 2. Parameter Decoding & Flag Recovery
Extracted the Base64 payload from the note URL parameter (`c3Bvb2t5e3RoZV9naG9zdF9sZWZ0X2FfdHJhY2V9`).

Decoding the string revealed the final flag: `spooky{the_ghost_left_a_trace}`
