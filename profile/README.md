# BuddhiKernel

Control infrastructure for autonomous AI agents: deciding **when to act, when to ask, and when to stop**.

Agent frameworks are good at making agents run. They are less good at deciding whether an agent should run at all, how much to spend on it, and when a human needs to be pulled in. BuddhiKernel is the layer that makes those decisions explicit, bounded and auditable.

## Projects

### [buddhi](https://github.com/buddhikernel/buddhi) · Apache-2.0 · Python

```bash
pip install buddhikernel
```

A composable supervisor kernel that rations cognition across agentic work.

For each unit of work it decides whether the item is worth acting on, how much model effort to spend, whether the stream has converged, whether to route to a model or to human judgment, and whether the spend fits inside a bounded hierarchical budget. The kernel defines the interfaces it depends on and deliberately implements none of them, so policy, routing, storage and escalation stay yours.

### [buddhi-review](https://github.com/buddhikernel/buddhi-review) · MIT · Python

```bash
pip install buddhi-review
```

A working application of the kernel: multi-vendor pull-request review.

Fans a PR out to reviewers from different labs, classifies each finding, applies fixes, and re-reviews until a round comes back clean or the round budget runs out.

The premise is measurable, and it was measured. In an internal benchmark on Claude-generated code, the multi-vendor panel found **681 valid bugs**; Claude reviewing its own work found **3.8%** of them, and **50.1%** surfaced only in round two or later, after fixes had been applied. Method and figures are in the [repository README](https://github.com/buddhikernel/buddhi-review#readme).

## How they fit together

The kernel holds all judgment logic. Adapters hold I/O and nothing else. `buddhi-review` is the reference adapter and it is deliberately thin: it talks to GitHub, and the kernel decides what to do.

The licensing follows the same split. The kernel is Apache-2.0 so it can be embedded and extended freely; the adapter is MIT.

## Status

Both projects are under active development and their interfaces may change. Each repository states its current stability, version and release notes; PyPI carries the published releases.

## Who

Built and maintained by [Manasvi Srivastava](https://github.com/m-s-21).
Contact: hello@buddhikernel.com
