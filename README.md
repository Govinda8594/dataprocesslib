# dataprocesslib
Designing a core component for an internal data processing library used by multiple teams. The library processes streams of domain events and must be correct, thread-safe, and memory-efficient.

Build & Run
- Set Java 17 and Maven for build.
- Run tests: mvn test or just run the test file
Design Decisions
- Used ConcurrentHashMap for thread safety as an alternative to simple HashMap
- Handling duplicates witha  ConcurrentHashMap pair of (id, set of timestamps) per ID
- Stream-based processing ensures memory efficiency.
- Parallel streams allow multi-threaded execution.
- Used the synchronized keyword to access one thread at a time.
Assumptions
- Deduplication is based on (id, timestamp) only.
- First occurrence of duplicate is processed, later ones ignored.
- Average is computed as sum/count.
