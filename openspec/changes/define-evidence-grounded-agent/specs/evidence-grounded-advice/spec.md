## ADDED Requirements

### Requirement: Source-aligned recommendations
The system SHALL select forecasts matching the requested township and interval that were issued and available at decision time, and expose missing coverage.

#### Scenario: Destination differs from home
- **WHEN** a resident requests advice for a different township
- **THEN** the system retrieves forecast evidence for that township and states the applicable interval

#### Scenario: Forecast coverage is incomplete
- **WHEN** an interval lacks eligible forecast records
- **THEN** the answer identifies the uncovered interval without fabricating conditions

### Requirement: Evidence and confirmation traceability
The system SHALL retain measurement and receipt times, evidence identifiers, and separate operation confirmations from comfort reports and recommendation acceptance.

#### Scenario: Concurrent or unconfirmed operations
- **WHEN** multiple devices operate or confirmation is absent
- **THEN** the system preserves overlapping states and leaves unconfirmed states unknown

### Requirement: Background event monitoring
The system SHALL group sustained changes and respect prompt cooldowns without bridging material sample gaps.

#### Scenario: Sensor reconnects
- **WHEN** a material gap interrupts the observation window
- **THEN** the system marks the window incomplete and restarts it

#### Scenario: Recent clarification
- **WHEN** an event needs a label but the cooldown has not elapsed
- **THEN** the system does not issue another prompt

### Requirement: Chronological pilot evaluation
The evaluation SHALL compare fixed rules and a shallow decision tree on identical held-out events and report evidence consistency, tool correctness, acceptance and clarification burden using the manuscript's stated denominators.

#### Scenario: Event crosses split boundary
- **WHEN** an event or feature window overlaps the development/test boundary
- **THEN** it is excluded from the comparison

#### Scenario: Confirmation arrives after prediction
- **WHEN** a later reply establishes the target state
- **THEN** that reply is not used as a predictor for the same state
