# Chen Siyu / daneeller

> Define the problem before choosing the tool.
> 先定义问题，再选工具。

I prefer to state what a problem is and where its constraints lie before talking
about tools. The conclusion often differs from the conventional answer. What I have
built is modest, but each piece is meant to be reproducible, verifiable, and open
for someone else to continue.

我不习惯先贴标签再说会什么。更愿意先讲清楚一件事到底要解决什么、约束在哪里，然后才谈
工具——结论常常与惯例不同。做过的东西不算多，但每一件都尽量可复跑、可验证、能被别人
接着做下去。

## How I Work / 我怎么做事

Four principles, stated briefly. / 几条反复验证过的原则，简述如下。

- **Constraints before solutions.** The answer depends on real limits, not on industry
  habit. Setting labels aside and reasoning from the constraints often leads somewhere
  else.
  **先问约束，再谈方案。** 答案取决于真实的限制，而非行业惯例。放下标签、从约束重新
  推导，结论常与惯例不同。

- **End to end, by myself.** From interface and data to inference and packaging, I go
  through each layer myself. Not to prove breadth, but because crossing every layer is
  how you find where a problem actually sits.
  **端到端自己走完。** 从界面、数据到推理与打包，每一层都自己穿过。不是为了证明覆盖面，
  而是只有穿过每一层，才知道问题卡在哪里。

- **Repeatable gates over "looks fine."** Tests, baselines, mutation smoke checks:
  confirm the gate turns red before trusting its green. Stability comes from repeated
  triggering, not a few observations.
  **可复跑的门禁胜过"看着差不多"。** 测试、基线、变异冒烟——先确认门禁能抓到红，再信它
  给的绿。稳定性来自可重复触发，而非几次观察。

- **Turn what breaks into public knowledge.** When a framework misbehaves, I first
  separate my misuse from a real defect. If it is the latter, I reduce it to a minimal
  reproduction and report it upstream.
  **把踩过的坑变成公共财产。** 遇到框架问题，先分清用法错误还是真实缺陷；是后者就做成
  最小复现上报上游。

## Public Record / 公开记录

All entries below link to the original thread. / 以下每条都可点开核对。

### Contributions to Flet / 给 Flet 上游的贡献

- [PR #7101](https://github.com/flet-dev/flet/pull/7101) · **Merged** — two gaps in
  the official async docs; also led to a framework fix in
  [#7106](https://github.com/flet-dev/flet/pull/7106).
  **已合并** — 补官方 async 文档两处空白，并带出 #7106 框架修复。

- [Issue #7109](https://github.com/flet-dev/flet/issues/7109) →
  [PR #7110](https://github.com/flet-dev/flet/pull/7110) · **Merged** — `run_task()`
  exceptions were logged under `concurrent.futures` rather than `flet`.
  **已合并** — `run_task()` 异常记在 `concurrent.futures` 而非 `flet` logger。

- [Issue #7107](https://github.com/flet-dev/flet/issues/7107) — `Page.update()`
  thread-safety contract was undocumented; `run_thread()` does not return to the UI
  thread.
  `Page.update()` 线程安全契约未文档化；`run_thread()` 并不回到 UI 线程。

- [Issue #7108](https://github.com/flet-dev/flet/issues/7108) →
  [PR #7113](https://github.com/flet-dev/flet/pull/7113) — unsafe cross-thread
  `asyncio.Event.set()` in the 1.x scheduler.
  1.x 调度器跨线程调用 `asyncio.Event.set()` 不安全。

- [Issue #7120](https://github.com/flet-dev/flet/issues/7120) — `run_thread()` workers
  could not be cancelled; the process lingered after the window closed.
  `run_thread()` worker 无法取消，关窗后进程滞留。

## Projects / 项目

| Project / 项目 | Description / 说明 |
|---|---|
| [ClassOrder / 课序](https://github.com/daneeller/course-order) | A semester timetable tool for HarmonyOS PC. Detects four classes of scheduling conflict and proposes actionable fixes.<br>面向鸿蒙 PC 的学期课表工具，查出四类排课冲突并给出可执行的改课方案。 |
| [Apache Commons CLI license scan](https://github.com/daneeller/f25015220-apache-commons-cli-license-scan) | Scanned 141 controlled files with ScanCode Toolkit 32.5.0, checking Apache-2.0 against LICENSE / NOTICE / file headers, including false positives and blind spots.<br>用 ScanCode Toolkit 32.5.0 扫完 141 个受控文件，核对 Apache-2.0 与 LICENSE / NOTICE / 文件头的一致性，并记录误报与盲区。 |

## Certifications / 认证

- HarmonyOS Developer Certification (Huawei) · HarmonyOS application development
  HarmonyOS 开发者认证（华为 · 鸿蒙应用开发）
- HCIA-AI (Huawei Certified ICT Associate – AI)
  HCIA-AI（华为认证人工智能工程师 · AI 方向）

## Contact / 联系

- GitHub: <https://github.com/daneeller>
- Site: <https://daneeller.github.io>
