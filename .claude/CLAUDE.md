# Claude principals must follow

1. always ultrathink for algorithms, performance related issues
2. always do online research and study
3. always add required tests
4. always check the build and all tests in both debug and release mode
5. always ask a proper agent for each individual sub tasks
6. always memorize the latest status in project root in local file named CLAUDE.md
7. always update the readme.md and all related documents once finished
8. use sequantial-thinking for research, study, debug tasks

### Core Beliefs

- **Incremental progress over big bangs** - Small changes that compile and pass tests
- **Learning from existing code** - Study and plan before implementing
- **Pragmatic over dogmatic** - Adapt to project reality
- **Clear intent over clever code** - Be boring and obvious

### Simplicity Means

- Single responsibility per function/class
- Avoid premature abstractions
- No clever tricks - choose the boring solution
- If you need to explain it, it's too complex

### Error Handling

- Fail fast with descriptive messages
- Include context for debugging
- Handle errors at appropriate level
- Never silently swallow exceptions

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

### When Stuck (After 3 Attempts)

**CRITICAL**: Maximum 3 attempts per issue, then STOP.

1. **Document what failed**:

   - What you tried
   - Specific error messages
   - Why you think it failed
   - update @ERROR.md, add this file exclusion in @.gitignore only if it's not

2. **Research alternatives**:

   - Do an online resarch and study
   - Find 2-3 similar implementations
   - Note different approaches used

3. **Question fundamentals**:

   - Is this the right abstraction level?
   - Can this be split into smaller problems?
   - Is there a simpler approach entirely?

4. **Try different angle**:
   - Different library/framework feature?
   - Different architectural pattern?
   - Remove abstraction instead of adding?

## Important Reminders

**NEVER**:

- Use `--no-verify` to bypass commit hooks
- Disable tests instead of fixing them
- Finish a job or task that doesn't compile
- Make assumptions - verify with existing code

**ALWAYS**:

- Update plan documentation as you go
- Learn from existing implementations
- Stop after 3 failed attempts and reassess

## Technical Standards

### Architecture Principles

- **Explicit over implicit** - Clear data flow and dependencies
- **Test-driven when possible** - Never disable tests, fix them

### Code Quality

- **Every job must**:
  - Compile successfully
  - Pass all existing tests
  - Include tests for new functionality
  - Follow project formatting/linting

## Decision Framework

When multiple valid approaches exist, choose based on:

1. **Testability** - Can I easily test this?
2. **Readability** - Will someone understand this in 6 months?
3. **Consistency** - Does this match project patterns?
4. **Simplicity** - Is this the simplest solution that works?
5. **Reversibility** - How hard to change later?

## Project Integration

### Learning the Codebase

- Find 3 similar features/components
- Identify common patterns and conventions
- Use same libraries/utilities when possible
- Follow existing test patterns

### Tooling

- Use project's existing build system
- Use project's test framework
- Use project's formatter/linter settings
- Don't introduce new tools without strong justification

## Quality Gates

### Definition of Done

- [ ] Tests written and passing
- [ ] Code follows project conventions
- [ ] No linter/formatter warnings
- [ ] Implementation matches plan
- [ ] No TODOs without issue numbers

### Test Guidelines

- Test behavior, not implementation
- One assertion per test when possible
- Clear test names describing scenario
- Use existing test utilities/helpers
- Tests should be deterministic

## for Rust test automation
- **Embrace Property-Based Testing:** Expand the use of `proptest` to more areas of the test suite, especially for integration and concurrency tests.
- **Strengthen Concurrency Tests:** Make concurrency tests to be more robust and less prone to non-deterministic failures.
- **Safety and Security Tests:** Add more targeted tests for memory safety and security, and consider using external tools like Miri.
- **Benchmark Accuracy:** Benchmark implementations to minimize noise and ensure they are measuring the intended functionality.
- **Code Organization:** Maintain a clear separation between tests and benchmarks by moving files to their appropriate directories.
- **IMPORTANT:** Only run benchmarks and performance tests against --release build.

## for Rust project

- cargo build: build the debug mode
- cargo test --lib: test the debug mode, exclude benchmarks and performance tests
- cargo build --release: build the release mode
- cargo test --release: test the release mode, test benchmarks and performance tests in release mode only
- cargo bench: run benchmarks
- always run `cargo build && cargo test --lib` to check failures and provide a fix
- always run `cargo build --release && cargo test --release` to check failures and provide a fix

