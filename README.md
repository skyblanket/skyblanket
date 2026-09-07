## Akash Chandran

**I write agent runtimes — the scheduler, supervision and state layer underneath the frameworks.**

Most people building with agents work at the framework layer. I work at the layer below: process
scheduling, supervision trees, state machines, and the verification gates that decide whether an
agent is safe to turn on.

### What I've built

**[swarmrt](https://github.com/skyblanket/swarmrt)** — A native runtime and compiler for concurrent
programs. BEAM-shaped: lightweight processes, supervision trees, message passing, preemptive
scheduling. **55K lines of C across 96 files, zero dependencies.** Plus `sw`, the language that runs
on it.

**[swarm-code](https://github.com/skyblanket/swarm-code)** — A terminal coding agent written in
`sw`, running on swarmrt. No Node, no Python.

**carbine** *(private)* — A BEAM-native coding agent that runs on your own endpoint.
Bring-your-own-model, whitelabel-ready.

**[o](https://github.com/skyblanket/o)** — An autonomous software loop. Watches its own board,
dispatches coding agents, verifies with real tests, auto-merges green work, auto-reverts
regressions, budgets itself daily.

**[swift-render](https://github.com/skyblanket/swift-render)** — Programmatic motion graphics in
Swift. SwiftUI scenes + Metal shaders → MP4.

### Background

- **ex-Head of Edge AI, Sarvam AI**
- **ex-CTO, Collectiv AI** — shipped a coding agent in 2023, on GPT-3.5, back when the model would
  not reliably hold a tool schema, keep call ordering straight, or preserve state across turns. The
  three failure classes below are ones I fixed by hand back then, before any framework existed to
  hide them.
- Building in AI since the GPT-2 evals days
- Now at **Otonomy Corp** — autonomy stacks for GPS-denied navigation and onboard perception

### Agent teardowns

If your agent works in a pilot and stalls in production, it is almost never the model. It is one of
three things:

1. **Context assembly** — the fact it needed was absent, buried, or evicted before the model saw it
2. **Tool arguments and ordering** — right tool, loosely-typed argument, or an ordering constraint
   that lives in the prompt instead of the schema and fails under load
3. **State across turns** — two tools mutating the same object, half-applied on retry, so the model
   is handed state that no single tool wrote

Send me one failing trace and I will spend 90 minutes telling you which one it is. Free, no deck.
If the finding is worth acting on we can talk about the fix; if not, you keep the finding.

**akash@otonomy.ai**
