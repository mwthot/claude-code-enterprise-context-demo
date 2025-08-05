# claude-code-enterprise-context-demo

This simulated enterprise repo demonstrates advanced Claude Code usage in large, multi-language codebases. It mirrors real-world complexity—microservices, shared libraries, infrastructure—while embedding Claude artifacts like scoped memory files, permissioned configs, and specialized subagents. The layout showcases how Claude can operate safely and effectively across deep project structures, supporting context continuity, modular workflows, and high-trust automation.


```
claude-code-enterprise-context-demo/
├── README.md                         # The story and demonstration guide
├── docs/                             # Enterprise documentation
│   ├── architecture-overview.md      # System design decisions
│   ├── development-workflow.md       # Team processes
│   └── service-dependencies.md       # Integration patterns
├── infrastructure/                   # Deployment and configuration
│   ├── docker-compose.yml            # Local development setup
│   ├── kubernetes/                   # Production deployment configs
│   └── monitoring/                   # Observability configuration
├── services/                         # Microservices implementation
│   ├── user-service/                 # Core user management
│   ├── product-service/              # Product catalog
│   ├── order-service/                # Order processing
│   └── payment-service/              # Payment processing
├── shared/                           # Common libraries and utilities
│   ├── common-types/                 # Shared TypeScript definitions
│   └── testing-utils/                # Shared testing frameworks
├── .claude/                          # Project-level Claude Code configuration
│   ├── settings.json                 # Project permissions and environment
│   ├── agents/                       # Custom subagents
│   └── CLAUDE.md                     # Project memory and context
└── context-management-examples/      # Demonstration scenarios
    ├── crisis-scenario/              # Context management breakdown and recovery
    ├── onboarding-journey/           # New developer experience
    └── cross-service-debugging/      # Complex debugging workflows
```

## Memory Hierarchy

### Project-Level Memory (`./CLAUDE.md`)

Notice how this project memory serves dual purposes: it provides Claude with architectural context while documenting decisions that human developers need to understand. The file references (@docs/, @infrastructure/) demonstrate how memory integrates with existing documentation rather than duplicating it.

### Service-Level Memory (`services/user-service/CLAUDE.md`)

This service memory demonstrates how context becomes more specific while building on project-level patterns. The file references provide immediate access to concrete implementation examples.

## Config Hierarchy

These configurations demonstrate sophisticated permission management that balances developer productivity with operational safety. The project-level config establishes broad guardrails while service-specific configs enable focused development work.

### Project level config

Project-level configuration establishes broad organizational guardrails that apply across the entire technology stack. This configuration allows reading of all relevant source files and permits common development operations like running tests, viewing git status, and executing build commands across multiple languages including Java, JavaScript, Python, and Go. However, it explicitly denies destructive operations such as file deletion, privilege escalation, and modifications to sensitive files like production configurations and dependency lock files. The configuration also establishes consistent environment variables for development work and includes an audit logging hook that tracks all command executions for compliance purposes.

### Service-specific config (`services/user-service/.claude/settings.json`)

Service-specific configuration for the user service builds upon the project foundation by providing more granular permissions tailored to Java and Spring Boot development workflows. This configuration allows writing to source code directories and test files while protecting build artifacts and production configurations from accidental modification. It enables specific Maven operations needed for service development, including compilation, testing, and local execution, while restricting deployment operations that could affect production environments. The configuration includes a post-edit hook that automatically applies code formatting using Maven Spotless, ensuring consistent code style without requiring manual intervention.

## Subagents

Subagents that demonstrate different categories of specialization while showing how they maintain architectural consistency. Each subagent should solve a specific class of enterprise development challenges.

### Database Expert (`.claude/agents/database-expert.md`)

Database Expert subagent focuses exclusively on database architecture and schema management within microservices environments. This subagent understands the complexities of designing database changes that maintain service independence while ensuring data consistency across service boundaries. When you delegate a task to this subagent, it applies specialized knowledge about PostgreSQL optimization, zero-downtime migration strategies, and performance considerations that would be difficult to maintain in a general development conversation. The subagent has restricted tool access limited to database-related operations, preventing scope creep while ensuring focused expertise.

### Security Reviewer (`.claude/agents/security-reviewer.md`)

Security Reviewer subagent specializes in identifying security vulnerabilities and ensuring compliance with enterprise security standards. This subagent evaluates code changes through the lens of OWASP security principles, privacy regulations like GDPR, and enterprise compliance requirements. Rather than requiring you to remember and apply complex security frameworks during regular development, you can delegate security analysis to this specialist that maintains consistent focus on authentication patterns, authorization logic, and data protection requirements.