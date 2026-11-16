# 01: Decide whether a pull request gets a PR-opened review

**What to build:** A maintainer can tell, for any pull request event, whether it should start one PR-opened review or be skipped in silence. A reviewable pull request in the same repository, with no implement mark and no published PR-opened review, produces the exact code-review dispatch: the same issue number a slash code review would use, the pull request number, the head branch, that pull request's base, the review loop left inactive, and chaining left off. A fork, a draft that was only opened, a pull request that is closed when the decision runs, an implement pull request, or a pull request that already has a PR-opened review produces no dispatch and no comment.

**Blocked by:** None (can start immediately).

**Status:** claimed

- [ ] A reviewable same-repository pull request with no implement mark and no published PR-opened review yields a dispatch payload
- [ ] The issue number is parsed from `branch_prefix/<id>-` on the head branch, and is the pull request number otherwise
- [ ] The payload carries the head branch name, not the SHA from the opening event, and the pull request's own base ref
- [ ] The payload marks the run as a PR-opened review, leaves the review loop inactive, and leaves chaining off
- [ ] A head branch in another repository is a silent skip
- [ ] An `opened` draft is a silent skip, and `ready_for_review` is not
- [ ] A pull request that is closed when the decision runs is a silent skip
- [ ] A body containing the implement mark `agent-pr-implement` is a silent skip
- [ ] Any existing review body containing `agent-pr-opened-review` is a silent skip, including a dismissed review
- [ ] Path filters are not a skip reason
- [ ] Events other than `opened` and `ready_for_review` are a silent skip
