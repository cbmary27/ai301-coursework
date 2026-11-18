Over the past week, I've been working on an open-source contribution to agntcy/dir, an open-source project that keeps a list of AI agents and checks each one for security problems.

I picked up one of the project's reported problems, which addressed an interesting limitation in how security checks were handled.

Previously, every new check erased the previous result. This meant there was no history of past checks, no way to see which checks were waiting or in progress, and no way for an admin to ask for a new check on demand.

Rather than jumping straight into coding, I first wrote a small automated test against the project's existing code to prove the problem was real.

The result? Only one check was available to look at. The earlier failed check had been erased.

A review tool I built to check my plans before I write code initially rejected my plan, because I had listed tests without saying how to run them or what results to expect. I revised the plan to include exact steps and expected results, and the second review passed.

I then built the fix so every check is saved in its own history, with its status and who asked for it, and added a way for admins to request a check and see past results. All the automated tests pass, and the same test that showed the problem now shows both checks saved.

This week I submitted my changes to the project as a pull request, and it's now waiting on feedback from the maintainers.

I'm looking forward to getting feedback on the implementation and continuing to contribute to the project.

A big takeaway from this experience: contributing to an existing open-source codebase involves much more than writing code. Understanding existing design decisions, communicating with maintainers, reproducing bugs, validating assumptions, and knowing what to defer are all part of the engineering process.

https://github.com/agntcy/dir/pull/2514

#OpenSource #SoftwareEngineering #Go
