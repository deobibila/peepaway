# Peepaway Architecture

Peepaway is an open-source travel planning platform. The goal is to make planning trips, organizing itineraries, and traveling with others a little easier.

We're keeping the architecture simple for now. As the project grows, we'll introduce new tools and patterns when there's a good reason to, not just because they're popular. (I hope i don't regret this)

## Repository Structure

Peepaway uses a monorepo to keep its applications in one place.

```text
peepaway/
├── apps/
│   ├── web/          # Next.js application
│   ├── backend/      # Future backend services
│   └── ios/          # Future native iOS application
├── docs/             # Project documentation
├── .github/          # GitHub Actions and repository configuration
└── package.json      # Root workspace configuration
```

The web application currently uses Next.js, React, and TypeScript. We use Yarn to manage the JavaScript workspace.

The backend and iOS applications are still being planned. Their architecture will be documented once development begins.

## Frontend Organization

The web application follows a feature-based structure.

- `src/app/` — Pages, layouts, and routing.
- `src/features/` — Feature-specific components, hooks, and logic.
- `src/components/` — Components shared across features.
- `src/hooks/` — Reusable hooks.
- `src/lib/` — Shared utilities and integrations.
- `src/providers/` — Application-wide providers.
- `src/config/` — Shared configuration.
- `src/types/` — Types used across multiple features.
- `src/test/` — Shared testing utilities.

These are organizational conventions, not a requirement to create every directory immediately.

Whenever possible, keep code close to the feature that uses it. For example, components used only for trip planning should live within the trip-planning feature rather than in the shared components directory.

## Development Principles

A few things we want to keep in mind as we build:

- **Keep things simple.** Avoid adding complexity before we actually need it.
- **Build with maintainability in mind.** Code should be easy for someone else to understand and contribute to.
- **Keep features independent where possible.** Changes to one feature shouldn't unnecessarily affect others.
- **Reuse code when it makes sense.** Avoid duplicate logic, but don't create abstractions for everything.
- **Test important functionality.** Add meaningful tests as features are implemented.
- **Document significant decisions.** If we make an important architectural choice, we should explain why.

## Contributing

Before introducing a new dependency, major directory, or architectural pattern, check whether the existing structure can support the change.

For larger changes, open an issue or discuss the approach in a pull request first.

See [CONTRIBUTING.md](../CONTRIBUTING.md) for development commands, branch naming conventions, and pull request guidelines.

## Moving Forward

This document will evolve alongside the project!

We don't need to figure out the entire system before building it. The idea is to start with a clean foundation, make thoughtful decisions, and improve things as we learn.