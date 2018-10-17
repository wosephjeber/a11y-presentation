# Accessibility (a11y)

This document is largely an aggregation of information and content from existing sources. I'm by no means an expert.

## What is a11y?
- Shorthand for "accessibility" (there are 11 letters between the "a" and the "y").
- The most concise definition I found is: "A subset of UX focused on making your websites usable by the widest range of people possible". (https://a11yproject.com/posts/myth-accessibility-is-blind-people/)

> Accessibility is often viewed as making your site work on screen readers. In reality, web accessibility is a subset of UX focused on making your websites usable by the widest range of people possible, including those who have disabilities.
> - source: https://a11yproject.com/posts/myth-accessibility-is-blind-people/

### Not just for blind people
  - Disabilities can be **visual** (blindness, low vision, color-blindness), **auditory** (deafness and hard-of-hearing), **motor** (inability to use a mouse, slow response time, limited fine motor control), or **cognitive** (learning disabilities, distractibility, inability to remember or focus on large amounts of information)
  - Disabilities can be temporary (e.g. broke an arm, lost your glasses)
  - Accessible interfaces give enabled users more options for interacting (such as using a keyboard if your mouse died but you want to complete your task, or using keyboard shortcuts to save time as a power user)

### Popular screen readers
  - [**VoiceOver**](https://www.apple.com/accessibility/mac/vision/) (Mac & iOS) - free, built in to the OS
  - [**NVDA**](https://www.nvaccess.org/) (Windows) – free
  - [**JAWS**](https://www.freedomscientific.com/Products/Blindness/JAWS) (Windows) - not cheap ($1000)

## Standards

### WCAG 2 (Web Content Accessibility Guidelines)
  - Defines principles, guidelines, and criteria to achieve different levels of a11y compliance.
  - Three levels: A, AA, AAA. A is the easiest to meet, AAA is the most difficult. At the AAA level, satisfying some criteria may come at the expense of other criteria and may not be feasible.

Principles:
- **Perceivable** – Information and user interface components must be presentable to users in ways they can perceive.
  - text alternatives for visual content (e.g. alt tags)
  - information, structure, and relationships conveyed through presentation can be programmatically determined or are available in text (e.g. semantic markup)
  - color is not the only visual means of conveying information
  - contrast is sufficient to read and distinguish content
- **Operable** – User interface components and navigation must be operable.
  - all functionality is operable via a keyboard
  - users have mechanisms for skipping content repeated on multiple pages (such as navigation)
  - pages have titles, sections have headings, inputs have labels, etc, so users can determine where they are
  - click targets are big enough for users to easily click on
- **Understandable** – Information and the operation of user interface must be understandable.
  - labels or instructions are provided when content requires user input
  - if an input error is detected, the item that is in error is identified and the error is described in text
  - a mechanism is provided for identifying the meaning of idioms, jargon, and abbreviations
- **Robust** – Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies.
  - using valid markup (no duplicate IDs, no invalid element nesting)

Helpful summary: https://www.w3.org/WAI/fundamentals/accessibility-principles/

### WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Application)
  - Special attributes that can be applied to HTML elements to provide special context and instructions to screen readers
  - Screen readers work with regular HTML, but ARIA attributes can provide screen reader users with more context and greater interactivity
  - Attributes exist for _roles_, _states_, and _properties_. Examples:
    - Role: `role="button"`
    - State: `aria-selected="true"`
    - Property: `aria-label="Close"`
  - DOM elements such as buttons, anchors, and inputs effectively have built-in ARIA attributes, so role and state attributes aren't necessary. Property attributes might still be useful in certain situations, such as providing a label for an input that doesn't have an `<label>` element, or providing text content for an button that only contains an icon.
  - ARIA has no effect on how elements are displayed or behave in browsers. It does not add new functionality and is meant to act only as an extra descriptive layer for screen readers.

Brief intro: https://a11yproject.com/posts/getting-started-aria/

### Bad ARIA is worse than no ARIA
  - Incorrect ARIA misrepresents visual experiences, with potentially devastating effects on their corresponding non-visual experiences. (https://www.w3.org/TR/wai-aria-practices-1.1/#no_aria_better_bad_aria)

## Practical applications

### Supporting keyboard users goes a long way
> For a web page to be accessible, all interactive elements must be operable via the keyboard.
> https://www.w3.org/TR/wai-aria-practices-1.1/#kbd_generalnav

  - If you can tab to and interact with an element with your keyboard, a screen reader can find and interact with the element as well.
  - The screen reader may need additional context about the element to communicate to the user, so keyboard navigation is not 100% sufficient, but it gets very close.

### Native DOM elements have a11y baked in. Use them whenever possible.
  - You can CSS to add hover and disabled states and use JS to add click handlers to static elements to make them interactive for mouse users, but keyboard users and screen readers won't be able to interact with them.
  - You can add `tabIndex` and `role` attributes and attach keypress event handlers to make elements interactive for keyboard and screen reader users.
  - Or you could just use a `button` or `a`, which have all of this behavior baked in.

### Should I use a button or link?
Not always a black and white decision, but in general:
  - If the element will perform navigation (load new page, refresh the page, jump to new content, etc), it should be a link.
  - If the element will perform some other action, such as submitting a form, triggering a modal or popup, changing the state of the application, it should be a button, etc.

### Helpful checklist
https://a11yproject.com/checklist

## Screen reader demo
  - Demonstrate using VoiceOver to interact with Efflux

## Resources
### Intros
- https://a11yproject.com/
- https://www.w3.org/WAI/fundamentals/accessibility-intro/
- https://webaim.org/intro/

### Standards
- https://www.w3.org/WAI/WCAG21/quickref/
- https://www.w3.org/WAI/standards-guidelines/wcag/
- https://www.w3.org/WAI/standards-guidelines/aria/
- https://www.w3.org/TR/wai-aria-practices-1.1

### Libraries/Frameworks
- https://ebay.gitbooks.io/mindpatterns/content/
- https://reach.tech/router
- https://ui.reach.tech/
