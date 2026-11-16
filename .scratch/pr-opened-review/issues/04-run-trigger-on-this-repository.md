# 04: Run the trigger on this repository

**What to build:** On this repository, a pull request that becomes reviewable in the same repository, and that the shared decision accepts, dispatches one code review through the existing phase workflow. The review's diff uses that pull request's base, and checkout uses the head branch tip. A manual code review keeps the base it uses today. Forks, drafts, closed pull requests, implement pull requests, and pull requests that already have a PR-opened review produce no comment. No new agent-config flag is added. Model credentials stay on the phase workflow. There is no slash comment to react to, and a missing comment id does not fail the run.

**Blocked by:**
- 01 — Decide whether a pull request gets a PR-opened review
- 02 — Publish at most one marked PR-opened review
- 03 — Mark an implement pull request at creation

**Status:** ready-for-agent

- [ ] This repository listens for `opened` and `ready_for_review` and calls the reusable gate with a runner input
- [ ] The gate uses the shared decision, then dispatches the existing phase workflow as a code review with the review loop inactive and chaining off
- [ ] The phase workflow accepts an optional comment id and a PR-opened review input, and passes the pull request base only for this trigger
- [ ] An empty comment id publishes no reaction
- [ ] Setup and the review job's runner stay on the consumer phase workflow
- [ ] A skipped pull request produces no comment
- [ ] Dogfood enables the trigger with no new agent-config flag
