---
description: How to maintain the project with a "Slow and Steady" mindset
---

# Philosophy: Slow and Steady Wins the Race

This workflow ensures that all AI-driven development on the Ravencoin fork follows an incremental, stability-first approach.

## Instructions for AI Agents

1. **Research First**: Before proposing any major dependency upgrades, research the minimum stable "stepping stone" version.
2. **Prioritize Compatibility**: If a dependency upgrade breaks the GUI (Qt), you MUST seek a version that maintains compatibility, even if it is not the absolute latest.
3. **Phase-Based Upgrades**: Structure all significant changes into phases.
    - **Phase 1**: Security and critical bug fixes using the most stable compatible versions.
    - **Phase 2**: Modernization and major version jumps only after Phase 1 is proven stable.
4. **Documentation**: Always update `PHILOSOPHY.md` if any new stable patterns are identified.
5. **No "Big Bang" Refactors**: Do not rewrite large sections of core logic in a single PR. Break refactors into small, testable chunks.

// turbo-all
## Verification
1. Run `make check` after every incremental upgrade.
2. Run functional tests: `python3 test/functional/test_runner.py`.
