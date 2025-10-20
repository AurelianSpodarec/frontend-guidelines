# Front-End Guidelines

_A practical approach to building scalable, maintainable front-end systems._

This README defines rules and best practices for the modern front-end workflow. The goal is to reduce cognitive load, prevent common mistakes, and build consistent, maintainable systems.

---

## Working with TypeScript

### Naming `type` and `interface`

To improve **IDE discoverability** and reduce **cognitive load**, every TypeScript type or interface is prefixed with `I` — regardless of whether it’s declared as a `type` or an `interface`.

**Why this helps**

- You don’t always remember whether a shape was defined as a type or interface; a consistent I prefix makes them easy to search, autocomplete, and recognize. Typing I in your IDE surfaces all interfaces and types for instant autocomplete.
- Prevents naming conflicts in frameworks like React, where components and their prop types often share names.
- Keeps codebases predictable, scalable, and easy to navigate — especially in large teams.

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

---

## Naming

### Component Naming

Files and components should be named with the type first, followed by the variant. This is the opposite of natural English word order, but it improves discoverability, predictability, and maintainability in modern front-end projects — even if it’s the opposite of natural English word order.

> NOTE: While some traditional style guides (e.g., Uncle Bob) recommend naming by variant then type, in modern front-end projects — with IDE autocomplete, AI-assisted tooling, and large component libraries — it is more practical to list the type first.

**Why this helps**

- Typing the component type (e.g., card) in your IDE immediately shows all related variants.
- Reduces cognitive load — you don’t need to remember the variant first.
- AI tools and automated systems can more easily filter and process components by type, reducing token usage and errors.
- Promotes a consistent and predictable file structure across the codebase.
- Works with uniquely named components — the principle is predictability, not fancy or arbitrary names.

```bash
# Bad
article-card
stats-card
card-box

# Good
card-article
card-stats
card-box
```

---

<!-- ## How to work with a Designers

### Align Tokens -->

<!-- ## Working with CSS & TailwindCSS

Follow a spacing bottom approach for a flow

## Accessability
 -->
