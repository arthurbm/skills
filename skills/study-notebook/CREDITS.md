# Credits

`study-notebook` is derived from [Matt Pocock](https://github.com/mattpocock)'s [`teach`](https://github.com/mattpocock/skills/tree/main/skills/productivity/teach) skill ([`mattpocock/skills`](https://github.com/mattpocock/skills), as of commit `ad5400b`). The teaching model is his: the workspace of `MISSION.md`, `RESOURCES.md`, `GLOSSARY.md`, learning records and `NOTES.md`; the split between knowledge, skills and wisdom; fluency against storage strength and desirable difficulty; the mission as the ground of every Lesson; the zone of proximal development read from learning records; Lessons that are short, tied to the mission and built around one tangible win; References as the compressed essence of Lessons; quiz options that give no clue; delegating wisdom to communities. `MISSION-FORMAT.md`, `RESOURCES-FORMAT.md`, `GLOSSARY-FORMAT.md` and `LEARNING-RECORD-FORMAT.md` are his files, carried over.

What changed:

- **Lessons are published in a Notebook** (a site of MDX pages with interactive Blocks and Visuals, a sidebar and a plan page) instead of standalone HTML files in `./lessons/`, `./reference/` and `./assets/`. The skill's terms (Notebook, Lesson, Reference, Block, Visual) are defined once, with Portuguese equivalents.
- **Session flow** (start, detours, end) with completion criteria, and **Building a Lesson** as ordered steps: primary-source extraction by a background subagent, plan, Visual, write, review in a browser and by a reviewer subagent, publish.
- **New files**: `LESSON-STANDARDS.md` (the quality bar the reviewer applies: the source's arc and the _why_, just-in-time prerequisites, literal quotes with pages, an interactive Visual, retrieval practice with Quiz and Recall), `SOURCES-FORMAT.md` (the `sources/` extraction that citations come from) and `NOTES-FORMAT.md` (the learner profile, which now holds the learner's preferences and outranks the skill's defaults, plus a format history).
- **Carried-over formats**, lightly edited: learning preferences moved from `MISSION.md` constraints to the profile in `NOTES.md`; `RESOURCES.md` entries record local paths and page offsets; `GLOSSARY.md` is written in the learner's language and points to the skill's own terms.
- **`VISUALS.md`**: the rules for explorable Visuals (learner-paced steps, predict-then-reveal, congruent and persistent motion), drawn from the learning-science sources it lists, with motion craft following [Emil Kowalski](https://emilkowal.ski)'s animation philosophy.
- **Scaffolding a Notebook** is a pending section, to be extracted from a real Notebook built on Fumadocs and Next.js.

The upstream license:

```
MIT License

Copyright (c) 2026 Matt Pocock

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Sources behind `VISUALS.md`

- Bret Victor, [Explorable Explanations](https://worrydream.com/ExplorableExplanations/) (2011): active reading, explorable examples.
- C. D. Hundhausen, S. A. Douglas and J. T. Stasko, "A Meta-Study of Algorithm Visualization Effectiveness", _Journal of Visual Languages and Computing_ 13 (2002), 259–290: how learners engage with a visualization matters more than what it shows. T. L. Naps et al. (ITiCSE 2002 working group) turned this into an engagement taxonomy, from viewing through responding, changing and constructing.
- B. Tversky, J. B. Morrison and M. Bétrancourt, "Animation: can it facilitate?", _International Journal of Human-Computer Studies_ 57 (2002), 247–262: the congruence and apprehension principles, and interactivity as the remedy.
- T. N. Höffler and D. Leutner, "Instructional animation versus static pictures: A meta-analysis", _Learning and Instruction_ 17(6) (2007), 722–738: animations help most when they are representational, depicting the change to be learned.
- R. E. Mayer and P. Chandler, "When learning is just a click away", _Journal of Educational Psychology_ 93 (2001), 390–397: learner-paced segments improve transfer. Mayer's _Multimedia Learning_ gives the segmenting, signaling, coherence and contiguity principles.
- P. Ayres and F. Paas, "Making instructional animations more effective: a cognitive load approach", _Applied Cognitive Psychology_ 21(6) (2007), 695–700: the transient information effect.
- Motion craft follows [Emil Kowalski](https://emilkowal.ski)'s animation philosophy ([animations.dev](https://animations.dev)).
