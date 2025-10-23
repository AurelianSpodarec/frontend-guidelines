# Front-End Guidelines - Writing In Progress

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

### Atomic Design

**Atomic Design** is a methodology popularized by **Brad Frost**, who’s done incredible work in the design system space. His framework gave a clear language and structure to something many teams were already doing — breaking interfaces down into small, reusable parts and building them back up into complete experiences.

> Note: This idea isn’t exclusive to Atomic Design. Many teams have independently arrived at similar approaches under different names. The power isn’t in the label — it’s in the mindset of **thinking modularly** and **designing systematically**. So whether you call it Atomic Design or something else, the principle remains the same.

Think of it in terms of **architecture**:

- **Atoms** are your basic materials — bricks, glass panels, wooden planks, steel beams.  
  In UI terms, these are the smallest reusable components: **buttons**, **inputs**, **labels**, **icons**.

- **Molecules** are small functional units — like a door, window, or staircase — built by combining several materials together.  
  In UI, that could be a **search bar** (an input + button) or a **form field** (a label + input + validation message).

- **Organisms** are larger, self-contained sections — such as an entire room or a building floor — formed by assembling multiple molecules.  
  In UI, this might be a **navbar**, **hero section**, or **product card** composed of multiple smaller elements.

- **Templates** are like architectural blueprints — they define the overall layout and how the rooms or sections connect.  
  In UI design, templates represent **page structures** or **layouts** that position organisms in a consistent way.

- **Pages** are the completed buildings — real, tangible environments where people live or work, built from all those smaller parts working together.  
  In UI, these are **final web pages** populated with real content and data, ready for users to interact with.

In short: whether you follow **Brad Frost’s Atomic Design** or your own naming system, the key idea is to **think in layers of abstraction**, **design for reuse**, and **build systems that scale** — from a single button all the way to an entire digital product.

---

#### Example: Atomic Design Folder Structure

```bash
css/
├─ 0-vendor/            # Third-party libraries such as TailwindCSS
├─ 1-tokens/            # Design tokens (colors, spacing, typography, components tokens)
│  ├─ theme-light/
│  │  ├─ primitives/    # Raw building blocks
│  │  │  ├─ colors.css  # color-blue-500
│  │  │  └─ spacing.css
│  │  ├─ semantics/     # Contextual or semantic tokens
│  │  │  ├─ colors.css  # color-primary
│  │  │  └─ spacing.css
│  │  └─ index.css      # Central entry for importing tokens
│  ├─ theme-dark/
│  └─ theme-coffee/
├─ 2-base/              # Base styles (normalize, global defaults)
├─ cheat.css            # Temporary Quick fixes
└─ styles.css           # Main entrypoint for all CSS imports
```

Using number prefixes in folder names keeps your CSS organized and ensures files are imported in a logical, predictable order. Unlike a normal computer, which sorts folders alphabetically, numbers let you control the cascade explicitly — from vendor files to tokens, base styles, and finally components.

This approach mirrors what CSS fundamentally is: a **cascade**. Styles at the top are loaded first, forming the foundation for everything that follows. By structuring folders from **primitives → semantics → base → components**, you align with that natural order, ensuring that:

- Core building blocks are defined first.
- Theme tokens and base styles layer correctly.
- Components can safely build on top without unexpected overrides.

This structure not only keeps your CSS scalable and predictable, but also mirrors the way your components evolve — from **atoms to pages** — ensuring your codebase grows as systematically as your design.

---

### CSS Methologies

For many years CSS was a wild west - there was no set of ways to do things, things was hard to write, it was messy, hard to modify and change things. So people were coming up with ways to manage this. And a few popular emerged, some of wich the concept is used till this day, maybe in a different form.

> Note: Depending on what you read, you’ll often find bias toward one methodology over another. The truth is, they’re all good — each solved real problems in its time. Your job isn’t to pick one “best” method but to understand them all and extract the best ideas from each. The real power comes from combining these approaches — whether it’s Atomic Design, BEM, or others — into a system that fits your team and product.

#### BEM

BEM is one of the most widely known CSS methodologies. It was created by developers at Yandex, a Russian company, and is documented at getbem.com.

BEM’s goal is to make your CSS modular, readable, and predictable by clearly defining relationships between components and their parts.

**Example:**

<!-- prettier-ignore -->
```css
.card {}
.card__title {}
.card--highlighted {}
```

- **Block** → a standalone entity (.card)
- **Element** → a part of the block (.card\_\_title)
- **Modifier** → a variation of the block or element (.card--highlighted)

This naming convention makes it easy to understand where each style belongs and helps avoid naming collisions as projects grow.

#### OOCSS

#### ITCSS

#### SMACSS

#### Further Resources

- **[Atomic Design by Brad Frost](https://atomicdesign.bradfrost.com/)**
  The original and most comprehensive resource on the Atomic Design methodology.

If you’re short on time, start with **[Chapter 2](https://atomicdesign.bradfrost.com/chapter-2/)** — it gives a concise, practical overview of the core concepts.

---

## Naming

### Component Naming

Files and components should be named with the type first, followed by the variant. This is the opposite of natural English word order, but it improves discoverability, predictability, and maintainability in modern front-end projects — even if it’s the opposite of natural English word order.

> Note: While some traditional style guides (e.g., Uncle Bob - The God Father of Programming) recommend naming by variant then type, in modern front-end projects — with IDE autocomplete, AI-assisted tooling, and large component libraries — it is more practical to list the type first.

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

What this does is increases double the work for something that can be solved once. Instead of designer thinking how to name a component, and then develoers thinking how to name the same component - you think of the name once and document it for good, and you create a culture where you systematise the namings of things - hard at first, but once you get used to it it becomes second nature and you start working like one body.

This also helps busienss create a culture and accountbality, where if someone quits, they dont take the insights with them, because its incraved in the culture and process, and anyone new to the company will have to adapt - to change something they will need to follow a democratic political process; this is usually thrown upon but that's how larger companies work. Even smaller companies can benefit from this - the key is to find balance..

#### Agree on Namings

Idealy have a person that oversees and governs the design ssytems, work as a democracy to add or take anything out.

Some challenges with working is when you have a Junior developer/desinger come in and they write a new component that might already exist and do what they wnated.

#### Align Tokens

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

### European Law

### UK Law

### American Law

## Tooling

### Husky

## Business Impact

Code is for business.
Prioritising.
MVP Costs. How and when to break desing.

## Security

### XSS Attacks

## Company Policies

Google sign in button

## Choosing a Framework

Psychology behind it

## Project Structure

No size fits all, adapt and use concept to create something that fits.

## Performance Optimization

## Git & Workflow

## Error Handling

## Design Systems