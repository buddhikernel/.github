# BuddhiKernel

Control infrastructure for autonomous AI agents: deciding **when to act, when to ask, and when to stop**.

Agent frameworks are good at making agents run. They are less good at deciding whether an agent should run at all, how much to spend on it, and when a human needs to be pulled in. BuddhiKernel is the layer that makes those decisions explicit, bounded and auditable.

## Projects

### [buddhi](https://github.com/buddhikernel/buddhi) · Apache-2.0 · Python

A composable supervisor kernel that rations cognition across agentic work.

Seven sequential decisions per item, including: whether it is worth acting on at all, which model and effort level to spend, whether the stream has converged, whether to route to a model or to human judgment, and whether the spend fits inside the budget.

Hierarchical budgets with per-subtree ceilings. Five seams the kernel defines but deliberately does not implement: `PolicyPack`, `Router`, `Store`, `EscalationTransport`, `OOBSource`.

### [buddhi-review](https://github.com/buddhikernel/buddhi-review) · MIT · Python

A working application of the kernel: multi-vendor pull-request review.

Fans a PR out to Claude, Codex, Gemini and Copilot, classifies each finding, applies fixes, and re-reviews until a round comes back clean or the round budget runs out.

Across 88 internal runs on Claude-generated code, the four-reviewer panel found **681 valid bugs**. Claude reviewing its own code found **3.8%** of them. **50.1%** surfaced only in round two or later, after fixes had been applied and the code re-read.

## How they fit together

The kernel holds all judgment logic. Adapters hold I/O and nothing else. `buddhi-review` is the reference adapter and it is deliberately thin: it talks to GitHub, and the kernel decides what to do.

The licensing follows the same split. The kernel is Apache-2.0 so it can be embedded and extended freely; the adapter is MIT.

## Status

`buddhi` is at v0.1.0. `buddhi-review` is alpha: end-to-end tested, not yet hardened across diverse repositories. CLI flags, output format and the Python API may change before v1.0.

## Who

Built and maintained by [Manasvi Srivastava](https://github.com/m-s-21).
Contact: hello@buddhikernel.com
