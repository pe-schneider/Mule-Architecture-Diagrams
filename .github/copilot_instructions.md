# Copilot Instructions: HTML Accessibility Review

When reviewing HTML pages, check for accessibility issues and prefer fixes that help keyboard users, screen reader users, low-vision users, and users with motion or cognitive sensitivities.

## Review goals
- Follow WCAG 2.1 AA as the default baseline.
- Prefer semantic HTML over ARIA.
- Flag anything that blocks keyboard access, screen reader comprehension, or visual readability.
- Recommend the smallest safe change that improves accessibility.

## What to check

### 1) Page structure and semantics
- Ensure there is exactly one clear `<h1>` for the page topic.
- Headings must follow a logical order; do not skip levels without reason.
- Use semantic landmarks where appropriate: `<header>`, `<nav>`, `<main>`, `<footer>`, `<aside>`.
- Prefer native elements such as `<button>`, `<a>`, `<label>`, `<input>`, `<select>`, `<textarea>` instead of div- or span-based controls.
- If a custom widget is used, verify it has proper keyboard support, focus handling, and accessible name/role/value.

### 2) Keyboard accessibility
- Every interactive control must be reachable and usable with the keyboard alone.
- Check for visible focus states on links, buttons, form fields, and custom controls.
- Flag keyboard traps, missing focus indicators, and controls that only work on hover or mouse click.
- Ensure the tab order matches the visual and logical reading order.

### 3) Images and media
- Informative images must have meaningful `alt` text.
- Decorative images should use empty `alt=""` and not be announced.
- Do not accept filenames or generic text like “image” as alt text.
- Video and audio content should have captions or transcripts when needed.
- Avoid autoplaying media with sound.

### 4) Forms and validation
- Every input must have an associated `<label>`.
- Placeholders are not a substitute for labels.
- Error messages must be specific, helpful, and tied to the relevant field.
- Required fields should be clearly identified in text, not only by color or icon.
- Validation feedback should be announced to assistive technologies when appropriate.

### 5) Links and buttons
- Link text must be descriptive out of context.
- Do not use “click here” or other vague phrases.
- Buttons should describe their action clearly.
- Do not rely on color alone to distinguish links or actions.

### 6) Color, contrast, and text
- Check that text contrast is sufficient for normal and large text.
- Do not use color as the only way to communicate status, selection, or errors.
- Ensure text can be resized without breaking the layout.
- Avoid tiny text, low-contrast placeholders, and thin gray text that is hard to read.

### 7) Dynamic content and ARIA
- Use ARIA only when native HTML cannot provide the needed behavior.
- Do not add ARIA roles, states, or properties that conflict with native semantics.
- If content changes dynamically, ensure the change is perceivable by screen readers when needed.
- Modal dialogs must trap focus, be dismissible with Escape when appropriate, and restore focus to the triggering element.

### 8) Navigation and orientation
- Provide a skip-to-content link when the page has repeated navigation.
- Navigation should be consistent across pages.
- Avoid unexpected context changes when a field receives focus.
- Ensure page language is declared with the `lang` attribute on `<html>`.

### 9) Common issues to flag
- Missing alt text on meaningful images.
- Form fields without labels.
- Custom controls that are not keyboard accessible.
- Poor color contrast.
- Missing focus styles.
- Inaccessible modals, menus, tabs, accordions, or carousels.
- Invalid or unnecessary ARIA usage.
- Heading structure that jumps or repeats without meaning.

## How to write review comments
- Be specific about the problem.
- Explain why it affects accessibility.
- Suggest a concrete fix.
- Prefer short, actionable feedback tied to the exact element or line.

## Suggested comment style
- “This control is only operable with a mouse. Please make it keyboard accessible and expose a clear focus state.”
- “This image appears informative, so it needs meaningful alt text instead of an empty attribute.”
- “This input has no associated label. Add a `<label>` so screen readers can identify it.”

## Review priority
1. Blockers: keyboard traps, missing labels, unusable controls, inaccessible dialogs.
2. High priority: poor contrast, missing alt text, broken focus order, invalid ARIA.
3. Medium priority: weak link text, unclear errors, inconsistent headings.
4. Nice-to-fix: minor semantic improvements and readability refinements.

## Default review stance
- Assume accessibility matters unless the element is clearly decorative or non-interactive.
- When uncertain, choose the more accessible option.
- If a page is both visually polished and accessible, say so clearly.

