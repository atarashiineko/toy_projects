## Folder Structure

A single root directory for all prompts: `/docs`
One folder per category and subcategory, formatted as `category.subcategory`
Example paths

```
/docs/seo.copywriting
/docs/marketing.ad-campaign
/docs/dev.debugging
```

## File Naming Convention

Format: `YYYY-MM-DD_prompt-name.vNNN.md`
Fields

* `YYYY-MM-DD` is the creation date in ISO format
* `prompt-name` is lowercase words separated by hyphens, no dots or spaces
* `vNNN` is a three-digit, zero-padded version number starting at `v000`
* `.md` is the file extension

## Language for Examples

All code examples must use **JavaScript**.

## Prompt Document Structure

### 1. Front Matter

Enclose in a YAML code block at the top. Include exactly these fields in this order

```yaml
---
id: category.subcategory.prompt-name.vNNN
title: Human Readable Title
description: One-sentence summary of intent and use case
tags:
- tag1
- tag2
created_date: YYYY-MM-DD
updated_date: YYYY-MM-DD
version: N
---
```

### 2. Content Sections

Begin each section with an H2 heading (`##`). Include these sections in order

## Prompt

Exact text to send to the LLM

## Parameters

One bullet per variable or placeholder used in the prompt

## Usage Example

Show sample user input and expected LLM output

## Notes

Optional guidance on tuning, edge cases, or performance

## Metadata Field Definitions

* `id` is a dot-delimited string matching folder, file name, and version
* `title` is Title Case, maximum 60 characters
* `description` is maximum 120 characters
* `tags` is a list of lowercase keywords, each maximum 20 characters
* `created_date` and `updated_date` use ISO date format (`YYYY-MM-DD`)
* `version` is an integer matching the file’s `vNNN` value

## Versioning and Updates

* Do not overwrite existing files
* To update a prompt, increment `version` by 1, update `updated_date`, and save as a new file
* Preserve all historical versions in the same folder

## Examples

### Folder Structure Examples

```
/docs
├── seo.copywriting
│   ├── 2025-06-08_keyword-analysis.v000.md
│   └── 2025-06-09_keyword-report.v001.md
├── marketing.ad-campaign
│   ├── 2025-05-20_facebook-headline-generator.v000.md
│   └── 2025-05-21_instagram-caption.v000.md
└── dev.debugging
    └── 2025-06-10_log-parser.v000.md
```

### Example Prompt File

```markdown
---
id: seo.copywriting.keyword-analysis.v000
title: Keyword Analysis for Blog Posts
description: Generate a list of long-tail keywords for a given topic
tags:
- seo
- keywords
- blogging
created_date: 2025-06-08
updated_date: 2025-06-08
version: 0
---

## Prompt
"Provide a list of 10 long-tail keywords related to '{{topic}}' with search intent labeled."

## Parameters
- `topic`: main subject or keyword phrase

## Usage Example
**Input**
User: "Generate long-tail keywords for topic 'electric vehicle maintenance'."
**Expected Output**
1. "EV battery health check tips"
2. "how to maintain electric car brakes"
…

## Notes
Ensure keywords focus on user intent rather than technical jargon.
```

## Points of Potential Confusion

* Folder names use exactly one dot to separate category and subcategory. Do not use additional dots.
* File names use an underscore between date and prompt-name. Do not replace with a hyphen.
* Prompt-name uses only hyphens to separate words. Do not include underscores, dots, or spaces.
* Version suffix is `.vNNN` immediately before `.md`. Always zero-pad to three digits.
* Dates are strictly `YYYY-MM-DD`. Do not include time or timezone.
