# Front-End Guidelines

_A practical approach to building scalable, maintainable front-end systems._

This README defines rules and best practices for the modern front-end workflow. The goal is to reduce cognitive load, prevent common mistakes, and build consistent, maintainable systems.

---

## Working with TypeScript

### Naming `type` and `interface`

To improve **IDE discoverability** and reduce **cognitive load**, every TypeScript type or interface is prefixed with `I` — regardless of whether it’s declared as a `type` or an `interface`.

**Why this helps**

- You don’t always remember whether a shape was defined as a `type` or an `interface`.
- There’s no strict rule on when to use one over the other.
- A consistent prefix (`I`) makes it easier to **search, autocomplete, and recognize** these structures in your codebase.
- Prevents naming conflicts in frameworks like React, where components and their prop types often share names.

```ts
// Bad
type OverlayPosition = "left" | "center" | "right";

interface ButtonProps {
  label: string;
  onClick?: () => void;
}

// Good
type IOverlayPosition = "left" | "center" | "right";

interface IButtonProps {
  label: string;
  onClick?: () => void;
}
```

**Benefits**

- Typing `I` in your IDE surfaces all interfaces and types for **instant autocomplete**.
- Promotes **consistent naming** and **reduces ambiguity** across the codebase.
- Keeps codebases **predictable, scalable, and easy to navigate** — especially in large teams.

---

<!-- ## Working with CSS & TailwindCSS

Follow a spacing bottom approach for a flow

## Accessability

## How to name things

Naming is hard. -->
