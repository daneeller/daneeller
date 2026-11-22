# Chen Siyu / daneeller

> Define the problem before choosing the tool.

I prefer to state what a problem is and where its constraints lie before talking
about tools. The conclusion often differs from the conventional answer. What I have
built is modest, but each piece is meant to be reproducible, verifiable, and open
for someone else to continue.

## How I Work

Four principles, stated briefly:

- **Constraints before solutions.** The answer depends on real limits, not on industry
  habit. Setting labels aside and reasoning from the constraints often leads somewhere
  else.
- **End to end, by myself.** From interface and data to inference and packaging, I go
  through each layer myself. Not to prove breadth, but because crossing every layer is
  how you find where a problem actually sits.
- **Repeatable gates over "looks fine."** Tests, baselines, mutation smoke checks:
  confirm the gate turns red before trusting its green. Stability comes from repeated
  triggering, not a few observations.
- **Turn what breaks into public knowledge.** When a framework misbehaves, I first
  separate my misuse from a real defect. If it is the latter, I reduce it to a minimal
  reproduction and report it upstream.

## Public Record

All entries below link to the original thread.

### Contributions to Flet

- [PR #7101](https://github.com/flet-dev/flet/pull/7101) · **Merged** — two gaps in
  the official async docs; also led to a framework fix in
  [#7106](https://github.com/flet-dev/flet/pull/7106).
- [Issue #7109](https://github.com/flet-dev/flet/issues/7109) →
  [PR #7110](https://github.com/flet-dev/flet/pull/7110) · **Merged** — `run_task()`
  exceptions were logged under `concurrent.futures` rather than `flet`.
- [Issue #7107](https://github.com/flet-dev/flet/issues/7107) — `Page.update()`
  thread-safety contract was undocumented; `run_thread()` does not return to the UI
  thread.
- [Issue #7108](https://github.com/flet-dev/flet/issues/7108) →
  [PR #7113](https://github.com/flet-dev/flet/pull/7113) — unsafe cross-thread
  `asyncio.Event.set()` in the 1.x scheduler.
- [Issue #7120](https://github.com/flet-dev/flet/issues/7120) — `run_thread()` workers
  could not be cancelled; the process lingered after the window closed.

## Projects

| Project | Description |
|---|---|
| [ClassOrder](https://github.com/daneeller/course-order) | A semester timetable tool for HarmonyOS PC. Detects four classes of scheduling conflict and proposes actionable fixes. |
| [Apache Commons CLI license scan](https://github.com/daneeller/f25015220-apache-commons-cli-license-scan) | Scanned 141 controlled files with ScanCode Toolkit 32.5.0, checking Apache-2.0 against LICENSE / NOTICE / file headers, including false positives and blind spots. |

## Certifications

- HarmonyOS Developer Certification (Huawei) · HarmonyOS application development
- HCIA-AI (Huawei Certified ICT Associate – AI)

## Contact

- GitHub: <https://github.com/daneeller>
- Site: <https://daneeller.github.io>
