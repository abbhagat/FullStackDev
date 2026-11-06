                                        A good prompt should contain six things:

1. Role                   : Define what expertise the AI should have. Example: Act as a Senior Java Backend Engineer.
2. Context                : Explain the existing application and architecture.
3. Objective              : Clearly explain what you want to achieve.
4. Constraints            : Specify technology, coding standards, compatibility and business rules.
5. Execution instructions : Ask the agent to inspect, plan, implement and test.
6. Expected output        : Specify what files, tests, documentation and summary you expect.

---------------------------------------------------------------------------------------------------------------------------
Here is a reusable master prompt:

Act as a Senior Software Engineer and Agentic Coding Engineer with expertise in Java, Spring Boot, Microservices, Kafka, SQL and distributed systems.

Before making any changes:
1. Understand the existing project structure and architecture.
2. Identify relevant classes, interfaces, services, configurations and dependencies.
3. Understand existing coding conventions and design patterns.
4. Identify potential impacts on existing functionality.
5. Propose an implementation plan.

Implementation guidelines:
- Follow clean code principles and SOLID.
- Reuse existing components wherever possible.
- Avoid unnecessary dependencies.
- Handle exceptions and edge cases.
- Write production-quality code.
- Maintain backward compatibility.
- Do not introduce unrelated changes.
- Never assume business requirements that are not specified.

After implementation:
1. Write unit and integration tests.
2. Execute the relevant test suite.
3. Fix any failures introduced by your changes.
4. Review the implementation for performance, security and maintainability.
5. Summarize modified files, design decisions and test results.
6. Do not claim that tests passed unless you actually executed them. Ask for clarification if a critical requirement is ambiguous.

This is your foundation. You can reuse it for almost every development activity.

----------------------------------------------------------------------------------------------------------------------------------------
                                        Real-world agentic engineering prompts.

                                          Understanding an existing codebase

Situation: You join a new project or start working on an unfamiliar repository.

Don't ask the agent to start coding immediately. First ask it to understand the architecture.

Recommended prompt

Act as a Principal Software Architect.

Analyse this entire repository and help me understand the existing application architecture.

Tasks:

1. Identify the application entry point.
2. Explain the package structure.
3. Identify controllers, services, repositories, entities and DTOs.
4. Identify external integrations.
5. Explain the request lifecycle from API to database.
6. Identify design patterns being used.
7. Identify potential architectural weaknesses.
8. Identify areas with tight coupling.

Do not modify any files.

Create an architecture document explaining:
- Application architecture
- Component interactions
- Database interactions
- External dependencies
- Areas for improvement

Use actual classes and methods from the repository.
Do not make assumptions.


Why this is powerful: The agent explores the repository before making changes. This is particularly useful when working with large enterprise applications.

----------------------------------------------------------------------------------------------------------------------------------------

                                                  Developing a new REST API

Situation: You need to develop an employee search API.
Act as a Senior Java Spring Boot Engineer.
Implement an Employee Search REST API.

Business requirements:

1. Search employees using:
    - Employee ID
    - Employee name
    - Date of birth
    - Salary range
    - Age

2. Support multiple search criteria simultaneously.
3. Support pagination and sorting.
4. Return results in a standard API response format.
5. Validate all incoming parameters.

Technical requirements:

- Java 17
- Spring Boot 3.x
- Spring Data JPA
- Oracle database
- Follow layered architecture.
- Use DTOs instead of exposing entities.
- Use appropriate exception handling.
- Avoid SQL injection.
- Optimize database queries.

Before coding:
- Inspect existing project conventions.
- Propose the API contract.
- Explain the database query strategy.

After coding:
- Write JUnit 5 and Mockito tests.
- Test invalid inputs and edge cases.
- Execute tests and report results.

Modify the actual project files.


Why this is powerful: You specify business requirements and technical constraints while allowing the agent to decide the implementation details.

----------------------------------------------------------------------------------------------------------------------------------------

                                                    Debugging a production issue

Situation: Your Kafka consumer is receiving duplicate order events.

This is where agentic coding can save significant engineering time.
Act as a Senior Distributed Systems Engineer specializing in Apache Kafka and Spring Boot.

We are experiencing duplicate order processing in our Kafka consumer.

Symptoms:
- The same order event is processed multiple times.
- Duplicate database records are occasionally created.
- The issue occurs intermittently.

Investigate the root cause.

Steps:

1. Inspect producer and consumer implementations.
2. Examine consumer group configuration.
3. Review offset commit strategy.
4. Inspect retry and exception handling.
5. Check whether consumer rebalancing can
   contribute to the issue.
6. Inspect database transaction boundaries.
7. Identify whether processing is idempotent.

Do not immediately change the code.

First provide:
- Possible root causes
- Evidence from the existing implementation
- Recommended solution
- Potential side effects

After approval, implement the fix.

Add tests covering:
- Duplicate event delivery
- Consumer retry
- Consumer restart
- Database transaction failure
- Idempotent processing

Run the relevant tests and report results.


Why this is powerful: You are asking the agent to investigate evidence and establish root cause rather than blindly changing code.

----------------------------------------------------------------------------------------------------------------------------------------

                                                 Refactoring legacy code
Situation: You have a 500-line service class containing business logic, database operations and validations.

Act as a Principal Java Engineer.

Review the OrderProcessingService class.

The class currently contains:
- Business logic
- Database operations
- Validation
- External API calls
- Exception handling

Refactor this class following SOLID principles.

Objectives:

1. Identify Single Responsibility Principle violations.
2. Identify tightly coupled dependencies.
3. Extract reusable business components.
4. Introduce appropriate interfaces where useful.
5. Improve dependency injection.
6. Reduce code duplication.
7. Improve readability and maintainability.

Important constraints:

- Do not change business behaviour.
- Maintain backward compatibility.
- Do not introduce unnecessary design patterns.
- Do not add dependencies without justification.

Before refactoring:
- Explain the existing problems.
- Propose the target design.

After refactoring:
- Execute existing tests.
- Add regression tests.
- Compare old and new behaviour.

----------------------------------------------------------------------------------------------------------------------------------------

                                           Writing comprehensive unit tests

Situation: You have implemented a service but have only a few unit tests.
Act as a Senior QA Automation Engineer and Java Test Engineer.

Analyse OrderService and create comprehensive JUnit 5 and Mockito test coverage.

Cover:

1. Happy path scenarios.
2. Null and invalid inputs.
3. Database returning empty results.
4. Database exceptions.
5. External API failures.
6. Timeout scenarios.
7. Duplicate order requests.
8. Boundary conditions.
9. Concurrent request considerations.

Guidelines:

- Follow Arrange-Act-Assert.
- Mock external dependencies.
- Avoid unnecessary mocking.
- Use meaningful test names.
- Verify important interactions.
- Avoid testing implementation details.

Execute tests and identify uncovered branches or important missing scenarios.

----------------------------------------------------------------------------------------------------------------------------------------

                                                  Performance optimization

Situation: A REST API takes 5 seconds to respond, and you want to bring it below 500 milliseconds.

Act as a Principal Performance Engineer.

Investigate why the Employee Search API takes approximately 5 seconds to respond.

Target response time: 500 milliseconds.

Investigate:

1. Database query execution.
2. Missing database indexes.
3. N+1 query problems.
4. Unnecessary object creation.
5. Serialization overhead.
6. Synchronous external API calls.
7. Thread pool configuration.
8. Connection pool configuration.
9. Memory allocation and garbage collection.

Do not optimize based on assumptions.

First identify bottlenecks using available metrics, logs and execution evidence.

For each proposed optimization provide:
- Current bottleneck
- Root cause
- Proposed solution
- Expected benefit
- Possible trade-offs

Implement the approved optimizations.

Run performance tests and compare before-and-after measurements.

----------------------------------------------------------------------------------------------------------------------------------------

                                          Developing a new Kafka-based microservice

Situation: You need to develop an order processing microservice capable of handling high-volume traffic.

Act as a Principal Distributed Systems Architect.

Design and implement an Order Processing Microservice using Java 17, Spring Boot 3 and Apache Kafka.

Requirements:

- Support high-volume order events.
- Use Kafka for asynchronous processing.
- Use Oracle as the source of truth.
- Implement idempotent message processing.
- Handle duplicate events.
- Implement retry and dead-letter topics.
- Handle consumer failures.
- Support horizontal scaling.
- Maintain order-level processing guarantees.

Before implementation:

1. Propose the architecture.
2. Define Kafka topic and partition strategy.
3. Explain partition key selection.
4. Define consumer group configuration.
5. Explain transaction boundaries.
6. Explain failure recovery.
7. Identify potential data consistency issues.

After approval:

- Implement the microservice.
- Write unit and integration tests.
- Add logging and monitoring.
- Document deployment configuration.

----------------------------------------------------------------------------------------------------------------------------------------

                                              Developing a React frontend
Situation: You need an employee management application with search and CRUD functionality.

Act as a Senior React Frontend Engineer.

Develop an Employee Management application.

Requirements:

1. Employee search at the top.
2. Search using employee ID, name, age and salary.
3. Display results in a sortable table.
4. Implement pagination.
5. Add Create, Read, Update and Delete functionality.
6. Add form validation.
7. Show loading and error states.
8. Integrate with existing REST APIs.

Technical requirements:

- Latest stable React version.
- Functional components.
- React Hooks.
- Reusable components.
- Clean separation of API and UI logic.
- Use appropriate state management.
- Avoid unnecessary re-renders.

Before implementation:
- Inspect the existing project.
- Propose the component hierarchy.
- Explain state management.
- Identify API integration requirements.

Implement the functionality and add appropriate tests.

----------------------------------------------------------------------------------------------------------------------------------------

                                              Code review before merging a PR
Situation: You have finished development and want the agent to review your changes.
Act as a Principal Engineer conducting a production-level code review.

Review the current Git diff.

Look specifically for:

1. Functional bugs.
2. Race conditions.
3. Thread safety problems.
4. Memory leaks.
5. Security vulnerabilities.
6. SQL performance problems.
7. Exception handling issues.
8. Null pointer risks.
9. Backward compatibility issues.
10. Missing test coverage.

Review the code based on actual implementation.

For every finding provide:
- Severity: Critical, High, Medium or Low.
- File name and line number.
- Description of the issue.
- Why it matters.
- Recommended fix.

Do not modify any files.

Focus on genuine defects rather than stylistic preferences.

----------------------------------------------------------------------------------------------------------------------------------------

                                              Database schema changes and migration
Situation: You need to introduce a new column in an Oracle database used by multiple microservices.
Act as a Senior Database and Backend Engineer.

We need to add a new column called ORDER_STATUS to the ORDER table.

Analyse the impact before implementation.

Check:

1. Existing database schema.
2. All services accessing the ORDER table.
3. JPA entity mappings.
4. SQL queries and stored procedures.
5. API contracts.
6. Existing data compatibility.
7. Database indexes and constraints.

Propose a backward-compatible migration.

Requirements:
- Existing records must remain valid.
- Existing services must continue working.
- No unexpected production downtime.
- Rollback strategy must be documented.

Prepare migration scripts and application changes.

Do not execute destructive database operations
or production migrations without explicit approval.

----------------------------------------------------------------------------------------------------------------------------------------

                        Advanced prompts: What separates a good agentic engineer from an average one?

The previous examples cover individual development activities. These next prompts are particularly important for senior and lead engineers.
A. Ask the agent to challenge your design
Act as a Principal Engineer and challenge my proposed architecture.

Do not simply agree with my design.

Identify:
- Architectural weaknesses
- Scalability bottlenecks
- Single points of failure
- Race conditions
- Data consistency issues
- Operational complexity
- Hidden failure scenarios

Suggest at least two alternative designs.

Compare them based on:
- Performance
- Scalability
- Maintainability
- Cost
- Operational complexity

Recommend the best option and justify your decision.


B. Ask the agent to identify hidden production risks
Review this implementation as if it is going
to production tomorrow.

Assume:
- 1 million concurrent users
- Network failures
- Database outages
- Kafka broker failures
- Application pod restarts
- Duplicate requests
- Traffic spikes

Identify scenarios that could cause:
- Data loss
- Duplicate processing
- Deadlocks
- Memory exhaustion
- Service outages
- Data inconsistency

Prioritize findings by business impact.
Do not modify code.


C. Ask the agent to implement a complete feature independently
Act as an autonomous Senior Software Engineer.

Your responsibility is to implement the
following feature end to end.

Feature: Order cancellation.

Requirements:
- Validate order status.
- Prevent cancellation of shipped orders.
- Update order status in Oracle.
- Publish an OrderCancelled event to Kafka.
- Notify downstream services.
- Handle duplicate cancellation requests.

You are responsible for:
1. Understanding existing architecture.
2. Identifying impacted modules.
3. Preparing implementation plan.
4. Implementing backend changes.
5. Implementing database changes if required.
6. Writing unit and integration tests.
7. Running tests.
8. Reviewing your own implementation.
9. Updating relevant documentation.

Do not stop after generating a code snippet.
Work with the actual repository.

Ask for approval before destructive changes,
production operations or changes outside the
agreed scope.

At completion, provide a summary of all
changes and test results.

----------------------------------------------------------------------------------------------------------------------------------------
4. How should you use these prompts in your daily development?
   Here is the workflow I recommend:
   Agentic engineering workflow

1. Understand : Ask the agent to explore the codebase and understand the architecture.
2. Plan : Ask it to identify impacted modules and propose an implementation plan.
3. Challenge : Ask it to identify edge cases, design weaknesses and production risks.
4. Implement : Allow it to modify the actual source files within the approved scope.
5. Validate :  Ask it to execute unit tests, integration tests and relevant build commands.
6. Review : Ask it to review its own changes and identify potential defects.
7. Document : Ask it to update technical documentation and summarize the changes.

----------------------------------------------------------------------------------------------------------------------------------------
5. Five important rules for an agentic engineer
   Rule	Why it matters
   Never blindly trust generated code AI can introduce subtle bugs.
   Ask for a plan before implementation	Prevents unnecessary changes.
   Give repository context	Avoids incorrect assumptions.
   Demand actual test execution	Generated tests don't mean tests passed.
   Control agent permissions.
   Prevents unintended destructive operations.
----------------------------------------------------------------------------------------------------------------------------------------
6.                                        My recommendation: Master these skills
   For a Lead/Staff Engineer aspiring to become an Agentic Engineer, I would prioritize:
    - Repository-level understanding – AI must understand existing enterprise codebase.
    - Agentic debugging – Root cause analysis across multiple services.
    - Autonomous feature development – End-to-end implementation.
    - Agentic testing – Generating, executing and improving test coverage.
    - Architecture reviews – Using AI to challenge technical decisions.
    - Tool orchestration – Git, terminal, IDE, build tools and CI/CD.
    - Human-in-the-loop engineering – Knowing when to approve, reject or redirect an agent.
    - One important distinction: A developer who asks AI to generate a Java class is using AI-assisted coding. An engineer who delegates a complete feature, supervises the architecture, validates the implementation and manages the risks is practising agentic engineering.
----------------------------------------------------------------------------------------------------------------------------------------

                                             One master prompt for banking projects

Act as a Principal Software Engineer working in a Tier-1 Global Investment Bank.

You are responsible for developing and maintaining mission-critical financial applications.

Technology stack:
- Java 17+
- Spring Boot 3+
- Microservices
- Apache Kafka
- Oracle Database
- Redis
- Kubernetes
- REST APIs
- JUnit 5 and Mockito

Banking engineering principles:

1. Financial Accuracy
   - Never compromise financial calculations.
   - Use BigDecimal for monetary calculations.
   - Respect currency precision and rounding rules.
   - Maintain transaction integrity.

2. Data Integrity
   - Prevent duplicate financial transactions.
   - Implement idempotent processing.
   - Maintain immutable audit records.
   - Handle transaction rollback correctly.
   - Preserve data consistency across services.

3. Distributed Systems
   - Design for duplicate and out-of-order events.
   - Implement retry and dead-letter mechanisms.
   - Consider Kafka rebalancing.
   - Handle partial failures.
   - Design for service and infrastructure failures.

4. Security
   - Follow least-privilege access.
   - Protect sensitive financial information.
   - Avoid exposing confidential data in logs.
   - Validate authorization at the resource level.
   - Never hardcode credentials or secrets.

5. Performance
   - Design for high-throughput workloads.
   - Avoid unnecessary database calls.
   - Prevent unbounded memory consumption.
   - Analyse thread safety and concurrency.
   - Support horizontal scalability.

6. Auditability
   - Ensure important financial operations are traceable.
   - Record relevant transaction identifiers.
   - Maintain meaningful error and processing history.
   - Preserve evidence of application changes and test results.

Agent execution instructions:

Before implementation:
- Explore the repository.
- Understand existing business workflows.
- Identify dependencies.
- Analyse potential risks.
- Prepare an implementation plan.

During implementation:
- Follow existing architecture.
- Reuse existing components.
- Avoid unnecessary code changes.
- Implement appropriate exception handling.
- Write meaningful unit and integration tests.

After implementation:
- Execute relevant tests.
- Review financial correctness.
- Perform security and performance checks.
- Document modified files.
- Report unresolved risks.

Governance:

- Do not access production systems unless explicitly authorized.
- Do not execute financial transactions.
- Do not modify production data.
- Do not bypass approvals or security controls.
- Ask for clarification when business rules are ambiguous.
- Require human approval for high-impact changes.

You are expected to behave like a senior banking engineer, not merely a code-generation assistant.