# Front-End Guidelines

_A practical approach to building scalable, maintainable front-end systems._

This README defines rules and best practices for the modern front-end workflow. The goal is to reduce cognitive load, prevent common mistakes, and build consistent, maintainable systems.

> Note: To view the full content of this article, locate the README file above (marked with an open book icon). On the same line, click the three-line button on the right to expand and access the full content.

---

## TypeScript

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

## CSS

### Atomic Desing Folder Structure

```bash
css/
├─ 0-vendor/            # Third-party libraries or resets
├─ 1-tokens/            # Design tokens (colors, spacing, typography, components)
│  ├─ theme-light/
│  │  ├─ primitives/    # Raw building blocks
│  │  │  ├─ colors.css
│  │  │  └─ spacing.css
│  │  ├─ semantics/     # Contextual or semantic tokens
│  │  │  ├─ colors.css
│  │  │  └─ spacing.css
│  │  └─ index.css       # Central entry for importing tokens
│  ├─ theme-dark/
│  └─ theme-coffee/
├─ 2-base/              # Base styles (normalize, global defaults)
├─ cheat.css            # Utilities, overrides, quick fixes
└─ styles.css           # Main entrypoint
```

Using number prefixes in folder names keeps your CSS organized and ensures files are imported in a logical, predictable order. Unlike a normal computer, which sorts folders alphabetically, numbers let you control the cascade explicitly — from vendor files to tokens, base styles, and finally components.

This approach also mirrors what CSS is fundamentally: a cascade. Styles at the top are loaded first, forming the foundation for everything that follows. By structuring folders from primitives → semantics → base → components, you align with the cascade, ensuring that:

Core building blocks are defined first.

Theme tokens and base styles layer correctly.

Components can safely build on top without unexpected overrides.

Following Atomic Design, this order also helps establish a clear mental model: you can easily skin themes, add new components, and maintain a modular, scalable CSS architecture.

### Naming Methologies (BEM, OOCSS, ITCSS, SMACSS)

#### BEM

---

## Naming

### Component Naming

Files and components should be named with the type first, followed by the variant. This is the opposite of natural English word order, but it improves discoverability, predictability, and maintainability in modern front-end projects — even if it’s the opposite of natural English word order.

> Note: While some traditional style guides (e.g., Uncle Bob) recommend naming by variant then type, in modern front-end projects — with IDE autocomplete, AI-assisted tooling, and large component libraries — it is more practical to list the type first.

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

## Designers

Collaboration with designers is a crucial part of front-end development, even though it doesn’t involve creating design assets yourself or writing any code.

> Note: Front-end development is not design work. Your role is to translate design decisions into code, including colors, spacing, layout, accessible HTML, and API integration. Understanding front-end does not make you a designer — creating or adjusting colors, playing with visuals, or making design decisions is the domain of design. Design involves psychology, user research, and visual theory. Your job is to systematize these decisions consistently in code, building reusable, maintainable, and accessible interfaces.

### Collaborating

One of the biggest pitfall organisations make is they divide design and front-end into two separate sectors.

Desing and Front-end has many things in common:

- Naming Components
- Design System
- Naming Files

What this does is increases double the work for something that can be solved once. Instead of designer thinking of name and develoer you think of the name once and document it for good, and you create a culture where you systematise the namings of things - hard at first natural second. You start working like one body.

#### Agree on Namings

Idealy have a person that oversees and governs the design ssytems, work as a democracy to add or take anything out.

Some challenges with working is when you have a Junior developer/desinger come in and they write a new component that might already exist and do what they wnated.

### Align Tokens

## Accessability

Accessibility is about making information and digital experiences available to all people, regardless of their abilities or disabilities. Information is one of the most valuable resources in the modern world, and ensuring it is accessible means that everyone can use, understand, and benefit from it. Accessibility is not just about checking off boxes—it is about creating meaningful access for people who might otherwise be excluded from fully using the internet. For decades, and still today, many websites remain partially or completely unusable for individuals with accessibility challenges.

**Accessibility considerations are broad and can include:**

- Motor impairments: Designing interfaces that can be navigated without precise mouse control.
- Visual impairments: Supporting screen readers, high-contrast modes, and scalable fonts.
- Auditory impairments: Providing captions, transcripts, and alternative ways to access audio content.
- Cognitive impairments: Ensuring content is clear, consistent, and easy to navigate.

Because accessibility impacts so many users, it should be one of the first considerations when starting a project, not an afterthought. Designing with accessibility in mind from the outset saves time, reduces retrofitting costs, and ensures a more inclusive user experience.

There are numerous tools to help developers and designers assess accessibility, such as:

- WAC2 Chrome Plugin: Provides automated accessibility checks.
- Built-in Chrome Accessibility Tools: Chrome has recently expanded its suite of accessibility features, making it easier to evaluate websites directly in the browser.

Beyond the ethical and practical reasons, accessibility is increasingly a legal requirement. More countries are implementing laws that require websites to meet accessibility standards. In the past, launching a website without accessibility considerations was common, but today failing to comply can lead to lawsuits and financial penalties.

### UK Law

### European Law

### American Law
