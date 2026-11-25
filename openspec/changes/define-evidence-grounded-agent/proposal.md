## Why

Indoor measurements and outdoor forecasts describe different locations and time intervals. DietSense proposes evidence-grounded household recommendations rather than inferring appliance operation from humidity alone.

## What Changes

- Resolve activity, place and interval before selecting evidence.
- Track measurement and receipt times, operation confirmations and feedback separately.
- Group sustained changes into events and limit repeated questions.
- Define a chronological single-room pilot with fixed-rule and shallow-tree baselines.

## Capabilities

### New Capabilities
- `evidence-grounded-advice`: source-aware advice, monitoring and pilot evaluation.

### Modified Capabilities
- None; this is a proposed design.

## Impact

Affects the proposed ESP32/MQTT acquisition, SQLite storage, Python analysis and language-model routing. No deployment or measured results are claimed.
