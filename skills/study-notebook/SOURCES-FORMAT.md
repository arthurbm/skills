# sources/ Format

`sources/` holds what the Lessons cite, extracted from the primary sources: literal quotes, exact pages, exact examples. It lets a Lesson be written, and reviewed, without re-reading the source. One file per source unit (a chapter, a spec section, a talk), named `<source>-<unit>.md`, such as `zatsiorsky-ch3.md`.

## Template

```md
# Sources: {source title}, {unit}

{One paragraph: full citation and edition, the page convention (e.g. "book p. X / PDF p. Y, where PDF = book + 12"), the language the quotes stay in, and any fix applied to the extracted text.}

---

## {Id}. {Section number and title} ({pages})

**Arc**
- {The problem the section starts from.}
- {The example it uses and how it develops.}
- {Where it arrives.}

**Quotes**
- "{Literal excerpt.}" ({page})

**Exact examples**
- {Tables, code, numbers, steps, as the source gives them.} ({page})

**Secondary sources**
- {What the slides, lecture or docs show for this section, with page, and where they diverge from the primary source.}

## Checked while writing

- {A fact verified during writing: the quote, sentence or behaviour, and the path or command it came from.}
```

## Rules

- **Sections follow the source's order**, which is the order the Lesson follows.
- **Quotes are literal** and stay in the source's language; paraphrase lives in the Arc, without quotation marks.
- **Every quote and example carries its locator**: a page, a timestamp, or a section anchor for web sources.
- **State the page convention once**, in the header. When the PDF page differs from the printed page, give the offset and cite both.
- **Check symbols against the page image** when extracted text scrambles them, and say in the header which ones were restored.
- **Record what you check yourself** under "Checked while writing" the moment you check it, so the reviewer can follow every claim to its origin.
