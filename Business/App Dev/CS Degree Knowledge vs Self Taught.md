
## What CS graduates know that self-taught devs often don't

  

### Theoretical Foundations

- **Data structures & algorithms** — not just usage, but *why* certain structures perform the way they do (e.g. hash map O(1) vs binary search tree O(log n)) and when to choose each

- **Big O notation** — formally reasoning about how code scales with input size

- **Computer architecture** — how CPUs, memory, caches, and registers work under the hood

- **Operating systems** — processes, threads, scheduling, memory management, syscalls

- **Networking** — TCP/IP, DNS, HTTP at the packet level, not just the API level

- **Compilers & interpreters** — how code becomes machine instructions; parsing, ASTs, optimization

- **Discrete math & logic** — set theory, graph theory, proofs, boolean algebra

- **Database theory** — relational algebra, normalization, query optimization, ACID vs BASE

  

### Software Engineering Practice

- Design patterns (factory, observer, singleton, etc.) and when to apply them

- Systems design — architecting things that scale to millions of users

- Version control theory — branching strategies, merge vs rebase (not just commands)

- Testing methodology — unit, integration, end-to-end, TDD, mocking

  

### Mental Models

- Thinking in **abstractions and layers** — formally separating concerns

- **Formal problem decomposition** — breaking vague problems into solvable subproblems

- Understanding **tradeoffs** deeply (consistency vs availability, memory vs speed)

  

---

  

## Do CS grads use tools like Supabase?

  

**Yes.** Knowing more means choosing the *right* tool, not the most complex one.

  

- **Supabase is appropriate for:** side projects, startups, MVPs, apps where Postgres + auth + storage covers your needs

- **More custom setups are for:** specific scaling requirements, unusual data models, fine-grained infrastructure control

  

### What a CS background adds when using Supabase

- Understanding what Supabase does under the hood (Postgres + PostgREST + GoTrue + storage)

- Knowing its limits — e.g. when Row Level Security becomes a bottleneck, or when to move off managed infra

- Writing better schemas — proper normalization, indexes, foreign keys

- Knowing *when not* to use it (e.g. if you need a graph DB or time-series DB)

  

### Key Insight

> Knowing more doesn't mean using harder tools. It means knowing *why* you're using a tool and *when to switch*. A senior engineer would happily use Supabase for a side project.

  

---

  

## Tags

#cs #programming #self-taught #backend #databases #supabase #knowledge