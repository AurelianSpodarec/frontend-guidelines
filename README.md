# Front-End Guidelines

_A practical approach to building scalable, maintainable front-end systems._

This README defines rules and best practices for the modern front-end workflow. The goal is to reduce cognitive load, prevent common mistakes, and build consistent, maintainable systems.

## Working with TypeScript

### Naming `type` and `interface`

Prefix all types and interfaces with `I` for **consistency and IDE discoverability**.

> Why? This ensures consistent autocomplete and prevents naming conflicts with components or other identifiers.

```ts
// Bad
type TOverlayPosition = "left" | "center" | "right";

interface Image {
  src: string;
  alt: string;
}

// Good
type IOverlayPosition = "left" | "center" | "right";

interface IImage {
  src: string;
  alt: string;
}
```

**Benefits:**

- Typing `I` in your IDE surfaces all interfaces/types for **quick autocomplete and search**.
- Prevents naming collisions (e.g., Button vs IButton).
- Avoids confusion about whether a shape is declared as a `type` or `interface`.
- Promotes **consistent naming** across the codebase, reducing cognitive load.

<!-- ## Working with CSS & TailwindCSS

Follow a spacing bottom approach for a flow

## Accessability

## How to name things

Naming is hard. -->
