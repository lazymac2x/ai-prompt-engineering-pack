# Developer Prompt Pack (20 Prompts)

> Battle-tested prompts for software engineers, architects, and DevOps professionals.
> Replace `{placeholders}` with your own context before use.

---

## 1. Deep Code Review

```
You are a senior software engineer conducting a thorough code review.
Review the following {language} code with focus on:
- Security vulnerabilities (injection, XSS, CSRF, auth issues)
- Performance bottlenecks and memory leaks
- SOLID principle violations
- Error handling gaps
- Race conditions or concurrency issues

Code to review:
{paste_code_here}

For each issue found, provide:
1. Severity (Critical / High / Medium / Low)
2. Line reference
3. Explanation of the problem
4. Concrete fix with code snippet
```

---

## 2. Root Cause Bug Analysis

```
I have a bug in my {language} application using {framework}.

Symptoms:
{describe_what_happens}

Expected behavior:
{describe_what_should_happen}

Environment: {os}, {runtime_version}, {relevant_dependencies}

Steps to reproduce:
{steps}

Relevant code:
{paste_code_here}

Please analyze this systematically:
1. List the top 3 most likely root causes, ranked by probability
2. For each cause, explain the mechanism that produces the observed symptoms
3. Provide a diagnostic step I can take to confirm or rule out each cause
4. Once identified, provide the fix with before/after code
5. Suggest a regression test to prevent this from recurring
```

---

## 3. Codebase Refactoring Plan

```
I need to refactor the following {language} code. The current problems are:
{list_problems — e.g., "god class", "deeply nested callbacks", "duplicated logic across 5 files"}

Current code:
{paste_code_here}

Constraints:
- Must maintain backward compatibility with {api_or_interface}
- Test coverage must not decrease
- Refactoring should be deployable in incremental PRs, not a big bang

Please provide:
1. A refactoring strategy with named design patterns to apply
2. Step-by-step execution plan (each step = one safe PR)
3. The refactored code for the most critical section
4. Migration notes for any callers/consumers of this code
```

---

## 4. System Architecture Design

```
Design a system architecture for the following application:

Product: {product_description}
Expected users: {user_count} concurrent users
Key requirements:
- {requirement_1}
- {requirement_2}
- {requirement_3}

Non-functional requirements:
- Availability: {target_uptime, e.g., 99.9%}
- Latency: {target, e.g., p99 < 200ms}
- Budget: {cloud_budget_per_month}

Please provide:
1. High-level architecture diagram (describe in text with component relationships)
2. Technology stack recommendation with justification for each choice
3. Data flow for the {primary_use_case}
4. Scaling strategy (what breaks first at 10x, 100x load)
5. Single points of failure and how to mitigate them
6. Estimated monthly infrastructure cost breakdown
```

---

## 5. REST API Design

```
Design a RESTful API for {resource_description}.

Domain context: {brief_business_context}
Consumers: {who_calls_this — e.g., "React SPA", "mobile app", "third-party integrators"}
Auth model: {auth_type — e.g., "JWT", "API key", "OAuth2"}

Please provide:
1. Resource naming and URL structure following REST best practices
2. Full endpoint list with HTTP methods, request/response bodies (JSON examples)
3. Pagination, filtering, and sorting strategy
4. Error response format with meaningful error codes
5. Rate limiting recommendations
6. Versioning strategy
7. OpenAPI 3.0 snippet for the two most critical endpoints
```

---

## 6. Database Schema Design

```
Design a database schema for {application_description}.

Key entities and their relationships:
{describe_entities — e.g., "Users have many Orders, Orders contain OrderItems, Products belong to Categories"}

Requirements:
- Database engine: {postgres/mysql/mongodb/etc.}
- Expected data volume: {estimates — e.g., "10M users, 500M orders"}
- Most frequent queries: {list_top_queries}
- Must support: {special_requirements — e.g., "soft deletes", "audit trail", "multi-tenancy"}

Please provide:
1. Complete schema with tables, columns, types, and constraints
2. Index strategy for the frequent queries listed above
3. Explanation of normalization decisions (and any intentional denormalization)
4. Migration SQL for the initial schema
5. Known trade-offs and what to watch as data grows
```

---

## 7. Comprehensive Testing Strategy

```
Create a testing strategy for {project_description}.

Tech stack: {language}, {framework}, {database}, {external_services}
Current state: {describe_current_test_coverage}
Team size: {number} developers

Please provide:
1. Test pyramid breakdown — recommended ratio of unit/integration/e2e tests
2. What to unit test vs. integration test (with concrete examples from my stack)
3. Mocking strategy for {external_services}
4. CI pipeline test stages with parallelization recommendations
5. Coverage targets per layer (and why 100% is or isn't the goal)
6. 5 example test cases for the most critical business logic: {describe_critical_flow}
7. Performance/load testing approach for {performance_sensitive_endpoint}
```

---

## 8. Docker & Container Optimization

```
Optimize the following Dockerfile for production deployment:

{paste_dockerfile}

Application type: {language/framework}
Base image currently used: {current_base_image}
Current image size: {size}
Build time: {current_build_time}

Please:
1. Rewrite the Dockerfile using multi-stage builds
2. Minimize final image size (target: under {target_size})
3. Optimize layer caching for faster rebuilds
4. Apply security hardening (non-root user, minimal attack surface, no secrets in layers)
5. Add health check instruction
6. Provide a matching .dockerignore file
7. Explain each optimization decision
```

---

## 9. CI/CD Pipeline Design

```
Design a CI/CD pipeline for {project_description}.

Repository: {monorepo_or_multi_repo}
Tech stack: {stack}
Cloud provider: {aws/gcp/azure}
CI platform: {github_actions/gitlab_ci/jenkins/etc.}
Environments: {dev, staging, production}
Team size: {number} developers, {deploy_frequency} deploys per week

Please provide:
1. Complete pipeline YAML/config file with all stages
2. Branch strategy (trunk-based vs. gitflow) with justification
3. Automated quality gates: linting, tests, security scanning, coverage thresholds
4. Deployment strategy: {blue_green/canary/rolling} with rollback procedure
5. Secret management approach
6. Notification/alerting on pipeline events
7. Estimated pipeline execution time per stage
```

---

## 10. Performance Profiling & Optimization

```
My {language} application has performance issues:

Symptoms: {describe — e.g., "API response time degraded from 50ms to 2s over 3 months"}
Infrastructure: {describe_setup}
Current metrics: {relevant_metrics}

Relevant code for the slow path:
{paste_code_here}

Please:
1. Identify the most likely performance bottlenecks in this code
2. Rank them by expected impact if fixed
3. Provide optimized code for the top 3 bottlenecks
4. Recommend profiling tools specific to {language} and how to interpret their output
5. Suggest infrastructure-level optimizations (caching, CDN, connection pooling, etc.)
6. Provide a monitoring query/dashboard setup to track improvements
```

---

## 11. Security Audit Prompt

```
Perform a security audit of the following {language} code that handles {sensitive_operation — e.g., "user authentication", "payment processing", "file uploads"}.

Code:
{paste_code_here}

Dependencies/packages used: {list_dependencies}

Check for:
1. OWASP Top 10 vulnerabilities applicable to this code
2. Authentication and authorization flaws
3. Input validation and sanitization gaps
4. Sensitive data exposure (logs, error messages, responses)
5. Dependency vulnerabilities (known CVEs)
6. Cryptographic weaknesses

For each finding, provide:
- Risk rating (Critical/High/Medium/Low)
- Attack scenario (how an attacker would exploit it)
- Remediation code
```

---

## 12. Legacy Code Migration Plan

```
I need to migrate legacy code from {old_stack} to {new_stack}.

Current system description:
{describe_current_system}

Reasons for migration:
{list_reasons}

Constraints:
- Zero downtime requirement: {yes/no}
- Timeline: {weeks/months}
- Team familiarity with new stack: {low/medium/high}
- Budget for parallel running: {budget}

Please provide:
1. Migration strategy (strangler fig, big bang, or hybrid) with justification
2. Phased execution plan with milestones
3. Data migration approach with rollback capability
4. Feature parity checklist generation approach
5. Risk register with mitigation for each risk
6. Testing strategy to validate equivalence between old and new
7. Cutover plan with go/no-go criteria
```

---

## 13. Code Documentation Generator

```
Generate comprehensive documentation for the following {language} code:

{paste_code_here}

Please produce:
1. Module/file-level docstring explaining purpose and design decisions
2. Function/method-level documentation with:
   - Description of what it does (not how)
   - Parameter descriptions with types and valid ranges
   - Return value description
   - Exceptions/errors that can be raised
   - Usage example
3. Inline comments ONLY where the logic is non-obvious
4. A "Architecture Decision" section explaining WHY this approach was chosen
5. A "Gotchas" section listing non-obvious behavior or edge cases

Output format: {jsdoc/docstring/rustdoc/javadoc/etc.}
```

---

## 14. Microservices Decomposition

```
I have a monolithic {language} application and need to decompose it into microservices.

Current monolith description:
{describe_modules_and_dependencies}

Current pain points:
{list_pain_points — e.g., "deploy takes 45 min", "one team's changes break another's features"}

Team structure: {describe_teams}

Please provide:
1. Service boundary identification using domain-driven design principles
2. Recommended service list with responsibilities for each
3. Inter-service communication patterns (sync vs. async, REST vs. events)
4. Data ownership strategy (which service owns which data)
5. Shared data handling approach (no shared databases!)
6. Migration sequence — which service to extract first and why
7. Infrastructure requirements (service mesh, API gateway, message broker)
```

---

## 15. Error Handling & Resilience Pattern

```
Design an error handling and resilience strategy for my {language} service that communicates with {external_services}.

Current error handling approach:
{describe_current_approach}

Failure modes I've observed:
{list_failure_modes — e.g., "downstream timeout", "rate limiting", "intermittent 500s"}

Please provide:
1. Error classification taxonomy (transient vs. permanent, retriable vs. non-retriable)
2. Retry strategy with exponential backoff implementation
3. Circuit breaker pattern implementation for {primary_external_service}
4. Fallback/degradation strategy for each failure mode
5. Structured error logging format for observability
6. Health check endpoint implementation
7. Complete code example integrating all patterns for one critical flow
```

---

## 16. Git Workflow & Branching Strategy

```
Design a Git workflow for my team.

Team: {team_size} developers
Release cadence: {frequency — e.g., "weekly", "continuous"}
Project type: {product_type — e.g., "SaaS web app", "mobile app", "library"}
Current pain points: {list — e.g., "merge conflicts", "broken main branch", "unclear what's in production"}
CI/CD: {ci_platform}

Please provide:
1. Branching strategy with visual branch diagram (text-based)
2. Branch naming convention
3. Merge strategy (merge commit, squash, rebase) with justification
4. PR review process and approval requirements
5. Release process from code freeze to production
6. Hotfix procedure
7. Example GitHub Actions / CI config that enforces this workflow
```

---

## 17. API Rate Limiter Implementation

```
Implement a rate limiting system for my {language} API.

Requirements:
- Limit: {requests_per_window} requests per {time_window}
- Scope: {per_user/per_ip/per_api_key}
- Algorithm preference: {sliding_window/token_bucket/leaky_bucket}
- Storage backend: {redis/in_memory/database}
- Must handle: {special_cases — e.g., "burst allowance", "different tiers", "whitelist"}

Please provide:
1. Core rate limiter implementation with the chosen algorithm
2. Middleware/decorator integration for {framework}
3. Response headers (X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset)
4. 429 Too Many Requests response format
5. Distributed rate limiting considerations if running multiple instances
6. Unit tests for edge cases (boundary, concurrent requests, clock skew)
```

---

## 18. Database Query Optimization

```
Optimize the following database query that is running too slowly:

Query:
{paste_query}

Table schemas:
{paste_relevant_schemas}

Current execution plan (EXPLAIN ANALYZE output):
{paste_explain_output}

Current execution time: {time}
Target execution time: {target}
Database: {postgres/mysql/etc.} version {version}
Table sizes: {row_counts}

Please:
1. Analyze the execution plan and identify the bottlenecks
2. Rewrite the query for optimal performance
3. Recommend indexes (with CREATE INDEX statements)
4. Suggest schema changes if the query can't be optimized in its current form
5. Provide the expected execution plan after optimizations
6. Note any trade-offs (write performance, storage, maintenance)
```

---

## 19. Monitoring & Alerting Setup

```
Design a monitoring and alerting strategy for {service_description}.

Infrastructure: {cloud_provider}, {orchestration — e.g., "Kubernetes", "ECS"}
Current observability: {what_exists_now}
SLA commitment: {uptime_target}

Please provide:
1. Key metrics to monitor (RED method: Rate, Errors, Duration) for each service
2. Infrastructure metrics (CPU, memory, disk, network) with thresholds
3. Business metrics that indicate system health
4. Alert rules with severity levels and escalation paths
5. Dashboard layout (what panels, what queries) for {grafana/datadog/cloudwatch}
6. On-call runbook template for the top 3 most likely incidents
7. Log aggregation strategy with structured logging format
8. Distributed tracing setup for request flow visibility
```

---

## 20. Technical Debt Prioritization

```
Help me prioritize and address technical debt in my {language} project.

Known tech debt items:
{list_items — e.g.,
- "No input validation on public API endpoints"
- "Test suite takes 45 minutes"
- "Hardcoded config values scattered across codebase"
- "Using deprecated library X"
}

Team capacity: {hours_per_sprint} hours per sprint for tech debt
Business context: {upcoming_features_or_scaling_needs}

Please:
1. Score each item on: Risk (if ignored), Effort (to fix), Value (once fixed) — using a 1-5 scale
2. Calculate a priority score and rank them
3. Group into "Quick Wins" (< 1 day), "Projects" (1-5 days), and "Epics" (> 5 days)
4. Create a sprint-by-sprint execution plan fitting within the capacity constraint
5. For the top 3 items, provide a concrete implementation approach
6. Identify any items that should block new feature work
```

---

*Part of the AI Prompt Engineering Pack v1.0.0*
*Created for professional developers who want to 10x their AI-assisted workflow.*
