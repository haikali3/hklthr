# MDX Blog Post Style Guide

A comprehensive reference for writing and maintaining blog posts in the hklthr repository.

---

## Table of Contents

- [Overview](#overview)
- [File Setup](#file-setup)
- [Front Matter Specification](#front-matter-specification)
- [Content Structure](#content-structure)
- [Formatting Guidelines](#formatting-guidelines)
- [Tone & Voice](#tone--voice)
- [Best Practices](#best-practices)
- [Quick Checklist](#quick-checklist)

---

## Overview

All blog posts in this repository use **MDX** (Markdown with JSX) format. MDX allows you to write standard Markdown content while optionally supporting React components for enhanced interactivity.

**Current approach:** Posts use pure Markdown—no JSX components. This keeps content portable and maintainable.

---

## File Setup

### File Location

```
data/blog/[post-slug].mdx
```

### Naming Convention

- Use kebab-case for filenames
- Examples: `ai-wrapper.mdx`, `fresh-grad-to-real-world-dev.mdx`
- Make the filename descriptive and SEO-friendly

### File Extension

Always use `.mdx` (not `.md`) for consistency with the project setup, even if you're only using Markdown features.

---

## Front Matter Specification

Every post **must** begin with YAML front matter enclosed by `---` delimiters.

### Complete Template

```yaml
---
title: 'Your Post Title Here'
date: '2026-01-17'
lastmod: '2026-01-17'
tags: ['tag1', 'tag2', 'tag3']
draft: false
summary: 'A concise 1-2 sentence summary of the post.'
---
```

### Field Definitions

| Field     | Type    | Required | Format                   | Description                                                        |
| --------- | ------- | -------- | ------------------------ | ------------------------------------------------------------------ |
| `title`   | String  | Yes      | 'Title in single quotes' | Post heading; appears in listings, search, and page title          |
| `date`    | String  | Yes      | 'YYYY-MM-DD'             | Original publication date; do not change once published            |
| `lastmod` | String  | Yes      | 'YYYY-MM-DD'             | Last modification date; update when significant revisions are made |
| `tags`    | Array   | Yes      | ['tag1', 'tag2']         | Search/filter categories; use lowercase, keep to 3-6 tags          |
| `draft`   | Boolean | Yes      | true \| false            | `true` = hidden from production; `false` = published               |
| `summary` | String  | Yes      | 'Summary text'           | Preview text for listings; 1-2 sentences max, no markdown          |

### Tag Conventions

Keep tags consistent and lowercase. Common examples from existing posts:

- Categories: `ai`, `career`, `guide`, `project`
- Technologies: `llm`, `gemini`, `golang`, `react`
- Themes: `reflection`, `mindset`, `growth`, `tutorial`

---

## Content Structure

### 1. Table of Contents (After Front Matter)

Create a manual table of contents with clickable anchor links to help readers navigate.

**Format:**

```markdown
## Table of Contents

- [Section Name](#section-name)
- [Subsection](#subsection)
  - [Nested Item](#nested-item)
```

**Rules:**

- Use `##` for the TOC heading
- Anchor links use lowercase with hyphens: `#section-name`
- Match anchor IDs exactly to your header IDs
- Include only major sections (not every subsection)

### 2. Headers

Use hierarchical structure:

- `##` = Major sections (main topics)
- `###` = Subsections (supporting points)
- Avoid `#` (reserved for page title)
- Avoid `####` and deeper (breaks visual hierarchy)

**Example:**

```markdown
## Main Topic

### Supporting Detail

Content here.
```

### 3. Paragraphs

- Keep paragraphs short (2-4 sentences)
- Use line breaks between paragraphs for readability
- Avoid walls of text

### 4. Lists

#### Unordered Lists (Bullet Points)

```markdown
- Item 1
- Item 2
  - Nested item
  - Another nested
- Item 3
```

#### Ordered Lists (Numbered)

```markdown
1. First step
2. Second step
   1. Substep
   2. Another substep
3. Third step
```

**Usage:**

- Use bullet points for non-sequential information
- Use numbered lists for processes or steps
- Indent nested items with 2 spaces

---

## Formatting Guidelines

### Text Emphasis

| Style    | Markdown                     | Use Case                                               |
| -------- | ---------------------------- | ------------------------------------------------------ |
| Bold     | `**text**`                   | Key concepts, important terms                          |
| Italic   | `_text_`                     | Emphasis, book/movie titles, non-English words         |
| Combined | `_You **can** combine them_` | When needed, but use sparingly                         |
| Code     | `` `code` ``                 | Function names, variables, commands, inline references |

**Examples:**

```markdown
The **API endpoint** requires _authentication_.

Use the `fetchUser()` function to retrieve data.

I learned that _**simplicity matters**_ in design.
```

### Code Blocks

#### Inline Code

```markdown
Use the `npm install` command to add dependencies.
```

#### Code Blocks with Language Highlighting

````markdown
```js
function greet(name) {
  console.log(`Hello, ${name}!`)
}
```
````

#### With Filename (Optional)

````markdown
```js:server.js
app.listen(3000, () => {
  console.log('Server running');
});
```
````

**Supported languages:** js, ts, jsx, tsx, py, go, rust, sql, bash, json, yaml, html, css, etc.

### Links

#### External Links

```markdown
[Link text](https://example.com)

Automatic link: https://example.com
```

#### Internal Anchor Links

```markdown
[Jump to Section](#section-id)
```

**Anchor ID rules:**

- Use lowercase letters, numbers, and hyphens only
- Replace spaces with hyphens
- Example: `## Real Progress` → `#real-progress`

#### Reference Links

```markdown
Check out [this guide][ref-guide] for more info.

[ref-guide]: https://example.com/guide
```

### Blockquotes

```markdown
> This is a blockquote.
> Great for highlighting important statements or quotes.
```

**Usage:** Sparingly for testimonials, emphasized statements, or inspiration.

### Horizontal Rules

```markdown
---
```

Use to separate major sections if needed, but prefer header structure instead.

---

## Tone & Voice

Your posts balance **personal reflection** with **technical clarity**. Here's the established voice:

### Key Characteristics

1. **Conversational**

   - Write as if explaining to a peer
   - Use contractions: "i didn't," "it's," "we're"
   - Lowercase acceptable at start of sentences in reflective moments
   - Avoid overly formal language

2. **Personal & Reflective**

   - Share genuine learnings, not just facts
   - Use "i," "we," "my" perspective
   - Include honest mistakes and failures
   - Connect technical concepts to human experience

3. **Scannable**

   - Short paragraphs (2-4 sentences)
   - Bullet points for multiple ideas
   - Headers break up content
   - Readers should grasp main points by scanning

4. **Honest**
   - Admit what you don't know
   - Acknowledge limitations
   - Avoid hype or exaggeration
   - Back up claims with examples

### Example Passages

❌ **Too formal:**

```
The implementation of multimodal language models facilitates advanced
image processing capabilities through prompt engineering methodologies.
```

✅ **Your style:**

```
tried using Gemini's safety settings. set everything to `BLOCK_NONE`,
but it still filtered results. not reliable or consistent.
```

---

## Best Practices

### Before Writing

- [ ] Choose a clear, narrow topic
- [ ] Decide on target audience (fellow developers, fresh grads, specific niche)
- [ ] Outline major sections and key points
- [ ] Set a realistic scope (avoid covering everything)

### While Writing

- [ ] Write the content first, add formatting second
- [ ] Create accurate table of contents with matching anchor links
- [ ] Use consistent terminology throughout
- [ ] Review headers for parallel structure
- [ ] Test all links (both external and internal)
- [ ] Use backticks for technical terms: `variable`, `function()`, `npm install`

### Before Publishing

- [ ] Set `draft: false` in front matter
- [ ] Update `lastmod` date to today
- [ ] Verify all anchor links work
- [ ] Check date format is YYYY-MM-DD
- [ ] Ensure summary is 1-2 sentences only
- [ ] Read through once for typos and clarity
- [ ] Confirm tags are lowercase and relevant

### SEO Considerations

- Use descriptive title (readers + search engines benefit)
- Make summary compelling (appears in previews)
- Use header hierarchy properly (H2, H3, not random jumps)
- Include relevant, lowercase tags
- Filename should reflect content (`ai-wrapper` not `post-123`)

---

## Quick Checklist

Use this before committing a new post:

````markdown
- [ ] Filename is kebab-case.mdx
- [ ] Front matter has all required fields (title, date, lastmod, tags, draft, summary)
- [ ] Title is in 'single quotes'
- [ ] Dates follow YYYY-MM-DD format
- [ ] draft is set to false (if publishing)
- [ ] summary is 1-2 sentences max, no markdown
- [ ] tags are lowercase and in ['array', 'format']
- [ ] Table of Contents is present and accurate
- [ ] All TOC anchor links match header IDs
- [ ] No `#` headers (only `##` and `###`)
- [ ] Paragraphs are short (2-4 sentences)
- [ ] Important terms use **bold** or `code`
- [ ] Code blocks have language specified (`js, `py, etc.)
- [ ] All external links are tested and correct
- [ ] Tone matches your voice (conversational, honest, personal)
- [ ] Content is scannable (headers, bullets, short paragraphs)
- [ ] No typos or grammar issues (read aloud if needed)
- [ ] Post follows existing post structure and style
````

---

## Examples

### Full Post Skeleton

```markdown
---
title: 'How I Built My First CLI Tool'
date: '2026-01-17'
lastmod: '2026-01-17'
tags: ['cli', 'golang', 'tooling']
draft: false
summary: 'Started with bash scripts. Ended up learning Go. Here's what I learned building a production CLI from scratch.'
---

## Table of Contents

- [The Starting Point](#the-starting-point)
- [Choosing Go](#choosing-go)
- [What I Learned](#what-i-learned)

## The Starting Point

i had a repetitive task that took 30 minutes by hand.
built a bash script. worked, but felt fragile.
wanted something more robust.

## Choosing Go

looked at several languages:

- **Python**: Easy, but packaging was a nightmare
- **Rust**: Powerful, but steep learning curve
- **Go**: Simple, fast compilation, built-in cross-platform support

went with **Go**.

## What I Learned

### Static Binaries Are Magic

Go compiles to a single binary. no runtime dependencies.
just copy the file. it works everywhere.

### Error Handling Is Explicit

Go forces you to handle errors. at first it felt verbose.
now i appreciate it. bugs are caught early.

### Deployment Is Trivial

built on macOS, tested on Linux, sent to Windows teammates.
everyone reported: "just works."

that's the win right there.
```

---

## Final Notes

This guide is your reference for consistency. As your blog grows, refer back to it when:

- Starting a new post
- Reviewing existing posts for updates
- Maintaining consistent tone and structure
- Onboarding others to contribute

Questions? Review the example posts:

- `ai-wrapper.mdx` (technical project narrative)
- `fresh-grad-to-real-world-dev.mdx` (personal reflection)
- `github-markdown-guide.mdx` (reference/tutorial)

Happy writing.
