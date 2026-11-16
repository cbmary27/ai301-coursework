Over the past week, I've been working on an open-source contribution to agntcy/dir, an open-source directory of AI agents that security-scans registered agents.

I picked up issue #1874, which addressed an interesting limitation in how security scans were handled.

Previously, every new scan overwrote the previous result. This meant there was no scan history, no visibility into pending or running scans, and no API to explicitly request a new scan.

Rather than jumping straight into implementation, I wrote a regression test on the original `main` branch.

The result? Only one scan was available for inspection. The previous failure had been overwritten.

My plan-check tool initially rejected my implementation plan because I had listed tests without providing runnable steps or expected results. I revised the test plan to include explicit commands and expected outcomes, and the second evaluation passed.

I'm looking forward to getting feedback on the implementation and continuing to contribute to the project.

A big takeaway from this experience: contributing to an existing open-source codebase involves much more than writing code. Understanding existing design decisions, communicating with maintainers, reproducing bugs, validating assumptions, and knowing what to defer are all part of the engineering process.

https://github.com/agntcy/dir/pull/{TBA}

#OpenSource #SoftwareEngineering #Go
