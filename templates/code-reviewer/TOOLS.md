# Code Reviewer Tools & Integrations

## Version Control

### git
- **Purpose**: Access code, history, diffs, and change context
- **When to use**: Reading PR changes, understanding commit history, checking previous implementations
- **Common operations**: `diff`, `log`, `show`, `blame`, `bisect`
- **Risk level**: Low (read-only)
- **Confirmation**: No

### GitHub API / GitLab API
- **Purpose**: Fetch PR details, comments, review data, and context
- **When to use**: Getting PR metadata, reviewing existing comments, understanding related issues
- **Common operations**: Get PR files, comments, review history
- **Risk level**: Low (read-only)
- **Confirmation**: No

## Language-Specific Linters & Formatters

### Python
- **pylint** — Comprehensive code analysis (style, errors, complexity)
  - When: Checking for common Python mistakes, style violations
  - Risk: Low (read-only analysis)

- **flake8** — Style guide enforcement (PEP 8)
  - When: Verifying code follows Python conventions
  - Risk: Low (read-only analysis)

- **black** — Code formatter (automated style fixes)
  - When: Assessing if code formatting is consistent
  - Risk: Low (read-only comparison)

- **mypy** — Static type checker
  - When: Validating type annotations and catching type errors
  - Risk: Low (read-only)

- **bandit** — Security vulnerability scanner
  - When: Identifying security issues in Python code
  - Risk: Low (read-only)

### JavaScript / TypeScript
- **eslint** — JavaScript linter and error finder
  - When: Checking for syntax errors, best practices, style violations
  - Risk: Low (read-only analysis)

- **prettier** — Code formatter
  - When: Assessing code formatting consistency
  - Risk: Low (read-only comparison)

- **typescript** — Type checker (for TypeScript)
  - When: Validating type correctness and catching type errors
  - Risk: Low (read-only)

- **tsc** — TypeScript compiler
  - When: Checking for compilation errors and type issues
  - Risk: Low (read-only)

### Java
- **checkstyle** — Style checking (Sun/Google style guides)
  - When: Verifying Java code conventions
  - Risk: Low (read-only)

- **spotbugs** — Bug finder (common mistakes and anti-patterns)
  - When: Identifying potential bugs
  - Risk: Low (read-only)

- **PMD** — Code smell detector
  - When: Finding code quality issues and violations
  - Risk: Low (read-only)

### Go
- **gofmt** — Code formatter
  - When: Checking formatting consistency
  - Risk: Low (read-only comparison)

- **golint / revive** — Style linter
  - When: Checking against Go conventions
  - Risk: Low (read-only)

- **go vet** — Built-in code analyzer
  - When: Finding suspicious constructs
  - Risk: Low (read-only)

### C/C++
- **clang-format** — Code formatter
  - When: Assessing formatting consistency
  - Risk: Low (read-only)

- **clang-tidy** — Static analyzer
  - When: Identifying bugs and style issues
  - Risk: Low (read-only)

### Rust
- **clippy** — Linter catching common mistakes
  - When: Finding idiomatic issues and performance problems
  - Risk: Low (read-only)

- **rustfmt** — Code formatter
  - When: Assessing code style
  - Risk: Low (read-only)

## Code Complexity & Quality Analysis

### SonarQube / SonarCloud
- **Purpose**: Comprehensive code quality metrics and smell detection
- **When to use**: Assessing overall code quality, tracking trends, finding technical debt
- **Metrics**: Complexity, duplication, test coverage, security vulnerabilities
- **Risk level**: Low (read-only analysis)
- **Confirmation**: No

### CodeClimate
- **Purpose**: Code quality and maintainability metrics
- **When to use**: Understanding code health, identifying hotspots
- **Risk level**: Low (read-only)
- **Confirmation**: No

### Cyclomatic Complexity Analyzers
- **Purpose**: Measure function complexity
- **When to use**: Identifying overly complex functions
- **Tools**: radon (Python), complexity (JavaScript), metrics (Java)
- **Risk level**: Low (read-only)
- **Confirmation**: No

## Security Analysis

### Dependency Checkers
- **OWASP Dependency-Check** — Identifies known vulnerabilities
  - When: Checking for vulnerable dependencies
  - Risk: Low (read-only)

- **Snyk** — Vulnerability scanning and remediation
  - When: Finding and prioritizing security issues
  - Risk: Low (read-only)

- **npm audit / yarn audit** — JavaScript dependency checker
  - When: Checking JavaScript dependencies
  - Risk: Low (read-only)

### Secret Scanning
- **git-secrets** — Prevents committing secrets
  - When: Checking for leaked API keys, credentials, tokens
  - Risk: Low (read-only scanning)

- **truffleHog** — Searches for secrets in git history
  - When: Detecting accidentally committed secrets
  - Risk: Low (read-only)

- **detect-secrets** — Identifies secret strings
  - When: Finding hardcoded secrets in code
  - Risk: Low (read-only)

### SAST (Static Application Security Testing)
- **Semgrep** — Open source static analysis
  - When: Custom vulnerability patterns specific to code
  - Risk: Low (read-only)

- **Fortify** — Enterprise security scanner
  - When: Comprehensive enterprise security review
  - Risk: Low (read-only)

## Test Analysis & Coverage

### Test Runners & Frameworks
- **pytest** (Python) — Testing framework
  - When: Running tests to validate code
  - Risk: Low (test environment)

- **jest** (JavaScript) — Testing framework
  - When: Running JavaScript tests
  - Risk: Low (test environment)

- **JUnit** (Java) — Testing framework
  - When: Running Java tests
  - Risk: Low (test environment)

### Code Coverage Tools
- **coverage.py** (Python) — Coverage measurement
  - When: Assessing test coverage percentage
  - Risk: Low (read-only)

- **nyc** (JavaScript) — Coverage reporter
  - When: Checking JavaScript test coverage
  - Risk: Low (read-only)

- **jacoco** (Java) — Coverage metrics
  - When: Measuring Java test coverage
  - Risk: Low (read-only)

## Documentation & Readability

### Documentation Generators
- **Sphinx** (Python) — Documentation generation
  - When: Reviewing documentation generation setup
  - Risk: Low (read-only)

- **JSDoc** (JavaScript) — Documentation standards
  - When: Assessing documentation quality
  - Risk: Low (read-only)

- **Javadoc** (Java) — API documentation
  - When: Checking documentation completeness
  - Risk: Low (read-only)

### Markdown Linters
- **markdownlint** — Markdown style checking
  - When: Verifying README and doc formatting
  - Risk: Low (read-only)

## Performance Profiling

### Profilers
- **cProfile** (Python) — Function profiling
  - When: Analyzing code performance bottlenecks
  - Risk: Low (profile-only)

- **Chrome DevTools** (JavaScript) — Browser profiling
  - When: Identifying web performance issues
  - Risk: Low (test environment)

- **Java Flight Recorder** — JVM profiling
  - When: Analyzing Java performance
  - Risk: Low (profile-only)

### Benchmarking Tools
- **pytest-benchmark** (Python) — Benchmark runner
  - When: Measuring performance regressions
  - Risk: Low (test environment)

- **bench** (Go) — Built-in benchmarking
  - When: Testing Go function performance
  - Risk: Low (test environment)

## Code Review Platforms

### GitHub Pull Requests
- **Purpose**: Review interface and collaboration
- **When to use**: Reviewing code changes in GitHub
- **Features**: Comments, suggestions, approval workflow
- **Risk level**: Low (review-only)
- **Confirmation**: No

### GitLab Merge Requests
- **Purpose**: Review interface for GitLab
- **When to use**: Reviewing changes in GitLab
- **Features**: Comments, suggestions, CI/CD integration
- **Risk level**: Low (review-only)
- **Confirmation**: No

### Bitbucket Pull Requests
- **Purpose**: Review interface for Bitbucket
- **When to use**: Reviewing code in Bitbucket
- **Features**: Comments, approval workflow, Jira integration
- **Risk level**: Low (review-only)
- **Confirmation**: No

## Repository & File Operations

### grep / ripgrep
- **Purpose**: Search code for patterns
- **When to use**: Finding usages, checking for anti-patterns, searching codebase
- **Common searches**: Similar implementations, hardcoded values, error handling patterns
- **Risk level**: Low (read-only)
- **Confirmation**: No

### diff tools
- **Purpose**: Compare code changes
- **When to use**: Understanding what changed between versions
- **Risk level**: Low (read-only)
- **Confirmation**: No

### AST Parsers
- **Purpose**: Parse code into abstract syntax trees
- **When to use**: Deep code analysis, pattern matching
- **Languages**: Tree-sitter (multiple languages), ast module (Python)
- **Risk level**: Low (read-only)
- **Confirmation**: No

## Documentation & Reference

### Language Documentation
- **Official Language Docs** — Reference for language features
  - When: Verifying correct usage of language features
  - Risk: Low (read-only)

### Design Pattern References
- **Refactoring.guru** — Design patterns and refactoring
  - When: Identifying patterns and improvement opportunities
  - Risk: Low (educational)

### Security Guidelines
- **OWASP Top 10** — Security vulnerability categories
  - When: Assessing security risks
  - Risk: Low (educational)

- **CWE** (Common Weakness Enumeration) — Weakness taxonomy
  - When: Understanding vulnerability types
  - Risk: Low (educational)

---

## Tool Usage Guidelines

### Before Every Review
1. Ensure you have access to the code repository
2. Check that linters/formatters are configured for the project
3. Understand the project's coding standards and conventions
4. Verify test environment is available for running tests

### Standard Review Workflow
1. Run version control tools to understand the diff
2. Run linters appropriate for the language(s) in the PR
3. Run test tools to validate functionality
4. Run security scanners if relevant
5. Use code analysis tools for quality metrics
6. Run coverage tools to assess test adequacy
7. Perform manual code review with language/domain expertise

### Performance Considerations
- Some analysis tools (especially SAST) can be slow on large codebases
- Consider running tool subset for CI/CD vs. detailed review
- Profile analysis tools to understand bottlenecks
- Cache results where possible

### False Positive Handling
- Linters can have false positives — evaluate with context
- Document suppressions with explanations
- Don't blindly accept all linter suggestions
- Use judgment to distinguish real issues from style nitpicks
