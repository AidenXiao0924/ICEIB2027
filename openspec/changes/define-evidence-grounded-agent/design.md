## Context

The manuscript describes modules M1–M8: resident context, query input, planning, acquisition/storage, Python analysis, domain rules, decision and feedback. The pilot is planned for one room over approximately two weeks.

## Goals / Non-Goals

**Goals:** auditable evidence, explicit uncertainty, event-level feedback and leakage-aware evaluation.

**Non-goals:** causal appliance identification from humidity alone, full thermal comfort assessment, multi-room generalization, or claims of completed experiments.

## Decisions

- Keep forecast issue time, validity interval and township distinct from sensor measurements; select evidence available at decision time.
- Keep confirmation revisions and concurrent appliance states; missing replies stay unknown.
- Use deterministic feature extraction with approved tool arguments and logged evidence IDs.
- Merge sustained events and enforce a prompt cooldown.
- Compare classifiers on chronologically held-out complete events; exclude boundary-crossing and overlapping feature windows.

## Risks / Trade-offs

Sparse confirmations may bias evaluation; report unknown and overlapping counts. A single sensor lacks full comfort inputs. Forecast coverage may not match the requested interval. Thresholds and cooldown are to be set before held-out evaluation.
