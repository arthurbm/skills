# Lesson standards

The quality bar for a Lesson. Write to pass it. The reviewer applies **every** rule below and every preference in the learner profile (`NOTES.md`), and lists each violation with the excerpt and a fix. Where the profile and a rule disagree, the profile wins; the reason behind each profile line is in the workspace's format history.

A good Lesson leaves the learner able to produce the win in its `LessonHeader` and to explain why each step of the mechanism is the way it is.

## Depth

- Follows the source's **arc**, in its order and with its examples (from `sources/`), retold in the learner's language. Every central concept reaches its _why_: a Lesson that lets the learner place an idea without being able to explain it has failed.
- When the mechanism has a formal reason (a short proof, a counting argument, a termination argument), it appears in short numbered steps.
- **Just in time**: every prerequisite concept the Lesson uses without being about it appears in a theory `Callout` at the moment of use, with what it is, a small example and why it matters here. The Lesson's own subject gets sections, not a box. The Callouts stay the minimum the Lesson needs, never a parallel course.

## Sources and citations

- Every important claim from a source appears in a quote block (`Book`) with the literal excerpt and its locator from `sources/`: section and page for a book, timestamp for a video, section anchor for a web page. A bare "(Author, p. 87)" counts only as a complement to something already shown.
- Every fact about a real tool, product, standard or practice has a source in `sources/` or `RESOURCES.md`. An unchecked fact is cut or marked as unverified.
- Pages, sections and quotes match `sources/`. Text in quotation marks is literal; paraphrase goes without them.
- The Lesson recommends one primary source to read or watch next: the best one in `RESOURCES.md` for this subject.

## Visual

- At least one Visual of the central mechanism, passing every rule in [VISUALS.md](./VISUALS.md); cite violations by rule number.

## Format

- One objective and one concrete win in `LessonHeader`. When the Lesson has both a reading part and a doing part (work on the learner's own project), `Part` marks each. A map Lesson with nothing to build may have only the reading part; its win is then a retrieval exercise.
- Short blocks; tables, lists and diagrams in place of long paragraphs; numbered steps in `Steps`; `Next` with the explicit next step.
- Analogies start from the learner's known ground (profile and learning records) and sit in a `Callout kind="idea"`. Every concept connects to the mission.
- One short real-world connection in a `Callout kind="connect"`: a real tool, product or practice, ideally with the design decision taken and the alternative rejected. A connection bigger than one box becomes a detour in `NOTES.md`.
- Links to the related Lessons and References.
- A reminder that the learner can bring follow-up questions to the agent.

## Practice

- **Quiz**: 3 or 4 questions. Options stay within one word of each other in length, and the correct one is neither consistently the longest nor the shortest. The correct position varies across questions, and formatting and order carry no clue. Each `why` explains the typical mistake.
- **Recall**: 2 or 3 questions answered from memory, each with a model answer. When earlier Lessons exist, at least one brings one of them back (spacing). When the mission includes defending choices (an exam, a design review, an interview), at least two take the form "why did you do it this way?" or "what would the alternative be?", and the model answer justifies, cites the source and weighs the alternative's trade-off.
- **Doing part**: something concrete in the learner's project, taken from the mission. Each decision the Lesson raises for that project becomes a `Decision` card whose "Record" line points to where the project keeps it.

## Language

- The learner's language from the profile, with its full spelling and diacritics; identifiers and technical terms stay in the original.
- Every acronym is spelled out at its first use in each Lesson, because each Lesson is read on its own.
- The canonical terms of the workspace `GLOSSARY.md` (and of the learner's project glossary, when the mission names one), in place of their _Avoid_ aliases.
