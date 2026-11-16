# 02: Publish at most one marked PR-opened review

**What to build:** When a code review runs as a PR-opened review and publishes, the published review carries the once-only mark `agent-pr-opened-review` as well as the usual code review mark. A manual code review does not carry that once-only mark. If a review body already has it, a later PR-opened review stops before announcing itself and before calling the model. A run that publishes no review does not write the mark, so a failed run can be tried again. The code review's existing failure comment, labels, startup comment, and run footer stay as they are for a review that actually starts.

**Blocked by:** 01 — Decide whether a pull request gets a PR-opened review

**Status:** claimed

- [ ] A published PR-opened review body contains both the code review mark and `agent-pr-opened-review`
- [ ] The fallback publisher writes the same once-only mark when it publishes a PR-opened review
- [ ] A code review that is not a PR-opened review does not contain `agent-pr-opened-review`
- [ ] When any existing review body already contains `agent-pr-opened-review`, the phase does not post a startup comment and does not call the model
- [ ] A run that publishes no review does not write `agent-pr-opened-review`
- [ ] Labels still follow the event the agent chose, including when GitHub publishes a requested-changes review as a comment because the App opened the pull request
