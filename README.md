# Eight Weeks Without the REM

When the REM suspended service between Brossard and Gare Centrale from July 5 to August 17 2025, the RTL (Réseau de transport de l'agglomération de Longueuil) put a shuttle bus network in place for the sake of service continuity.

Given the transit disruption, where did the people that relied on the REM go, and what did they do instead? Was the shuttle bus a part of the solution?

This notebook uses open GTFS data from the RTL to assess the shuttle system on based on coverage, frequency, and travel time.

---

## Research Questions

### Primary Question: *operational scope*

- Did the RTL shuttle system provide a meaningful replacement for REM service during the summer 2025 closure?
  -  as measured by:
     -   scheduled frequency
     -   travel time
     -   stop coverage.
- Where specifically did the REM riders go?
  - Did they take the shuttle services?
  - Did they try to bypass the closure with buses to the Yellow Line?
- or did they switch to driving/carpooling?

### Secondary Question: *strategic scope*

- Did the RTL anticipate demand for the replacement network? Specifically, did they increase frequency on the bus routes during the closure window relative to baseline (a scheduling decision visible in the GTFS feeds, and a meaningful proxy for expected demand)?

---

## Data Sources

| Dataset | Source | Purpose |
|---|---|---|
| RTL GTFS 20250623 | RTL open data | BASELINE: normal scheduled service before closure |
| RTL GTFS 20250707 | RTL open data | DURING CLOSURE: shuttle routes and frequency changes |
| RTL GTFS 20250825 | RTL open data | POST-CLOSURE: normal service restored |

---

## Notebook Structure

### 1. Data Setup
Load GTFS feeds. Define the closure window (July 5 - August 17, 2025) and the comparison period (same dates in 2024).

### 2. The REM Baseline

Extract normal REM service from the pre-closure GTFS feed. Profile the route: stops, scheduled headways, and end-to-end travel time (Brossard to Gare Centrale).

### 3. The Replacement Options

Extract replacement services from the mid-closure GTFS feed and profile two alternatives riders had:

**Shuttle service:** stop coverage, headways, and scheduled travel time vs. the REM baseline.

**Longueuil metro bus routes:** RTL routes serving Longueuil–Université-de-Sherbrooke (Yellow Line). Did RTL increase scheduled frequency during the closure relative to baseline? A frequency increase is visible in the GTFS feeds and would indicate the agency anticipated demand for the traditional bus/metro path as a bypass to the shuttle.

### 4. Gap Analysis

Three-way comparison: REM baseline vs. shuttle vs. Longueuil metro bus option:
- Did the shuttles serve all REM stations?
- How did headways compare across all three options?
- How much longer was each alternative journey?
- Theoretical capacity: buses vs. automated trains

### 6. What the Data Can and Can't Tell Us
- GTFS captures scheduled service, not actual real-time operations or ridership
- The strategic scope question is answered in terms of RTL's intentions, not outcomes

What better data would look like:
- Fare gate counts
- RTL passenger loads
- Anonymised trip plan data

---

## Key Limitations

- GTFS only reflects scheduled service, not actual operations (if a bus is stuck in traffic or edge cases where a bus breaks down, etc). On-the-ground reliability during the closure (traffic variance, bus bunching) is not captured.
- The secondary question is answerable from GTFS, but a frequency increase only confirms RTL planned for demand, not that riders actually used those routes.
- No ridership denominator: without REM or shuttle passenger counts, modal shift rates cannot be calculated, only directional signals.

---

## Environment

Requires [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run jupyter notebook
```
## AI Usage Disclosure

Anthropic's Claude Sonnet 4.6 was used for:
- general planning
- clarifying wording
- code questions and suggestions
- generating boilerplate code (cell output formatting, etc.).

All code was either written by the author or carefully reviewed and validated by the author prior to use.
The author is solely responsible for all data sourcing, statistical reasoning, methodological decisions, and interpretation.
