# Claude principals must follow

1. always ultrathink for algorithms, performance, debuging related issues
2. always do online research and study 
3. always add required tests
4. always check the build and all tests in both debug and release mode
5. always ask a proper agent for each individual sub tasks
6. always memorize the latest status in project root in local file named CLAUDE.md
7. always update the readme.md and all related documents once finished
8. use sequantial-thinking for research, study, debug tasks
9. GtiHub CLI `gh` is installed

## common workflow

- explore: ask search-specialist for online study and research, read project readme.md and other docs under doc foler. ask business-analyst to address any business requirements.
- plan: think hard to comiple a clear step-by-step to-dos. consult cloud-architect if it's a cloud native design, ask backend-architect for server side design. write a very detailed plan in file plan-claude.md. for later implementations, start from this plan-claude.md and mark the task status once done.
- code: ask the proper coding agent for specific programing language, Rust: rust-pro, Go/Golang: golang-pro, Java: java-pro, Python: python-pro, C: C-pro, C++: cpp-pro etc. Always ask performance-engineer for performance review: algorithms, data structures, multi-threads & concurrencies, IOs etc.
- test: ask test-automator to write automated tests, including unit tests, integration tests and benchmark tests
- code review: ask our code-reviewer agent for this job, make sure the tasks in plan-claude.md are fully implemented without bugs
- document: ask our content-marketer to keep all readme, docs up to date with the latest information and examples

## debug, issues

- ask incident-responder agent to identify the issue severity, do online study if required.
- ask the debugger agent to start investigate then try to fix the issue. update or add more tests if required. always verify the fix.

## for Rust project

- cargo build: build the debug mode
- cargo test: test the debug mode
- cargo build --release: build the release mode
- cargo test --release: test the release mode
- cargo bench: run benchmarks
- always run `cargo build && cargo test` to check failures and provide a fix
- always run `cargo build --release && cargo test --release` to check failures and provide a fix
