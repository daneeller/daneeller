# 陈思宇 / daneeller

> 先定义问题，再选工具。

我不太习惯先给自己贴标签再说自己会什么。更愿意先讲清楚一件事到底要解决什么、
约束在哪里，然后才谈用什么工具——很多时候结论和"通常怎么做"并不一样。
做过的东西不算多，但尽量让每一件都能复跑、能验证、能被别人接着往下做。

## 我怎么做事

几条我自己反复验证过的原则，比技能清单更能说明我会交付什么：

- **先问约束，再谈方案。** 一个问题的答案取决于真正的限制条件，而不是行业惯例。
  把标签和惯例先放一边，回到约束重新推一遍，经常能推出不一样的结论。
- **端到端自己走完。** 从界面、数据、推理到打包发布，能自己走通的就不拆给别人。
  不是为了证明全栈，是因为只有穿过每一层，才知道问题到底卡在哪一层。
- **用可复跑的门禁代替"感觉差不多"。** 写测试、设基线、做变异冒烟——先确认门禁
  真的能抓到红，再信它给的绿。稳定性不是靠观察几次，是靠能重复触发。
- **把踩过的坑变成公共财产。** 遇到框架层面的问题，先分清是我的用法错了还是框架
  真的有缺陷；确认是后者，就做成最小复现报上去，能修就修。

## 公开记录

下面这些都能点开核对，不是自我评价。

### 给 Flet 上游的贡献

都能点开核对。按"先定义问题、再拿证据说话"推进：

- [PR #7101](https://github.com/flet-dev/flet/pull/7101) **已合并**——补官方 async 文档一直
  缺的两点：首帧更新要让出事件循环、后台线程异常的归属。维护者重写后合并，CHANGELOG
  1.1.x 署名 `@daneeller`；它带出的一个真实框架 bug 由维护者在
  [#7106](https://github.com/flet-dev/flet/pull/7106) 修掉（230 行测试，已合并）。
- [Issue #7109](https://github.com/flet-dev/flet/issues/7109) →
  [PR #7110](https://github.com/flet-dev/flet/pull/7110) **已合并**——用异常日志定位到
  `run_task()` 的错误记在 `concurrent.futures` 而非 `flet` logger，按 `flet` 过滤会完全漏掉；
  维护者在 1.x 复现后合并修复，顺带补上 `run_thread()` 与 PubSub 订阅者异常不上报的缺口。
- [Issue #7107](https://github.com/flet-dev/flet/issues/7107)——对照 0.86.5 与 1.x 源码逐行
  核实：`Page.update()` 的线程安全契约从未被文档化，`run_thread()` 被普遍误读成"回 UI 线程"，
  实际进的是线程池。
- [Issue #7108](https://github.com/flet-dev/flet/issues/7108) →
  [PR #7113](https://github.com/flet-dev/flet/pull/7113)——1.x 调度器跨线程调用
  `asyncio.Event.set()` 不安全。修复由社区贡献者认领后，我在隔离环境做了独立 A/B 对照：
  同一份测试在未修复版一个失败、一个**挂死 90 秒**（硬超时才终止），应用补丁后 6/6 全绿、
  0.47s——证实缺陷可致事件循环挂死，另附三点边缘加固建议供对方斟酌。
- [Issue #7120](https://github.com/flet-dev/flet/issues/7120)——`run_thread()` worker 无法取消，
  关窗后进程仍被 join 而滞留。用干净 venv 装 `flet==0.86.5` 做最小复现 + 无 worker 对照组：
  带 worker 晚约 10 秒退出、对照约 0.2 秒，并给出从共享线程池到
  `shutdown(wait=False, cancel_futures=True)` 的源码链。

其中有一次是[我自己判断错了](https://github.com/flet-dev/flet/issues/7102)：把日志末尾的
`Session was garbage collected` 当成崩溃原因。维护者指出那只是窗口关闭的 INFO 症状。
我用日志证据复核后公开承认误判、修正结论——报告的价值不在于每次都对，在于能被证据纠正。

## 项目

| 项目 | 说明 |
|---|---|
| [课序 · ClassOrder](https://github.com/daneeller/course-order) | 面向鸿蒙 PC 的学期课表工具。不只是显示课表，还查出四类排课冲突并给可执行的改课方案，把问题发现提前到录入的当下。 |
| [Apache Commons CLI 开源许可测试报告](https://github.com/daneeller/f25015220-apache-commons-cli-license-scan) | 用 ScanCode Toolkit 32.5.0 扫完 141 个受控文件，核对 Apache-2.0 与 LICENSE / NOTICE / 文件头三要素的一致性，并记录误报与检测盲区。 |

## 认证

- HarmonyOS 开发者认证（华为 · 鸿蒙应用开发）
- HCIA-AI（华为认证人工智能工程师 · AI 方向）

## 联系

- GitHub：<https://github.com/daneeller>
- 个人主页：<https://daneeller.github.io>

---

欢迎交流。如果你也觉得"通常这么做"不够有说服力，大概能聊到一块儿去。
