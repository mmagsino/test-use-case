# QA Transformation Testing Proposal

A high level technology agnostic approach on testing using a CI/CD practice aimed at automating and streamlining the software development lifecycle. 

---

## Functional testing approach

### The test pyramid

                   /-------------------\
                  /   End-to-End Test   \
                 /-----------------------\
                /       UI Testing        \
               /---------------------------\
              /       Contract Test         \
             /-------------------------------\
            /      Integration Test           \
           /-----------------------------------\
          /             Unit Test               \
         /---------------------------------------\

The test pyramid is a way of thinking about how different kinds of automated tests should be used to create a balanced portfolio. Its essential point is that you should have many more low-level UnitTests than high level BroadStackTests running through a GUI.

[Martin Fowler](https://martinfowler.com/bliki/TestPyramid.html)

### The shift left paradigm

Shift-left testing[1] is an approach to software testing and system testing in which testing is performed earlier in the lifecycle (i.e. moved left on the project timeline). It is the first half of the maxim "test early and often".

[Wikipedia](https://en.wikipedia.org/wiki/Shift-left_testing)

### Ephemeral testing

Ephemeral testing refers to using short-lived, disposable environments for software testing. These environments are spun up on demand, mimic production systems, and are automatically destroyed after use — making them ideal for rapid, isolated, and cost-efficient testing. Ephemeral integration and contract testing on API gives us production like validation that is cost efficient with faster feedback.

![Ephemeral Testing](./ci-cd-workflow.png)

### Functional testing proposal

![SDLC](./Software-Development.png)

- Developer Code → pushed to repository.
- Build Process → compiles and packages the application.
- Code Quality Scan → ensures standards, static analysis, and coverage.
- Third-Party Library Scan → checks dependencies for known vulnerabilities (e.g., via tools like OWASP Dependency-Check, Snyk, or Trivy).
- Run Tests → executes unit, integration, contract, UI, and end-to-end tests.
- Review the code by the dev/tester.
- Deploy/Release → only if all checks pass.
This diagram highlights how **security** and **quality gates** are integrated into CI/CD pipelines before deployment.

This automation approach with shift left and micro test planning helps dev, tester, BA and other stakeholders aligned with the business objectives on every phase of the software lifecycle. Allowing the team to adapt and evolve to changes with minimal friction. Ephemeral testing using container technology makes testing repeatable as all dependency are bundled and can be test in any environment consistently. Enforcing code quality scan by automation help developers verify their work without the need for manual review on guidelines and governance. Making review more valuable for the correct implementation of feature and better design. Shift left makes testing cost effective by minimizing the e2e and ui testing. 

 
## Non-Functional testing approach

Automating CI/CD pipeline for performance and load testing should be in a near prod environment. Observability and metric tools should be setup to verify the performance under load. Tools for simulating bandwidth, stress, and spike. Dynamic and static security and validation against SLO and SLA should be added to the pipeline. Making the system more predictable under afformentioned condition.

### Non-Functional testing proposal

## Shared test environment challenges
