# Visuals

A Visual is where the learner **operates** the mechanism instead of reading about it: an _explorable_ explanation, in Bret Victor's sense. The learner steps through it, feeds it, predicts it and breaks it, and the understanding comes from that engagement. Watching an animation is the weakest level; every rule below pushes the learner up from viewing to responding and changing.

Build every Visual to these rules. The reviewer applies each one by number.

## Gate: does this need motion?

A Visual earns motion when the concept **is a change**: a process, an algorithm running, a state evolving, something moving from one place to another. Animations beat static pictures mainly when the changes themselves are what must be learned. A concept that is a structure with nothing changing (a taxonomy, a layout, a table of cases) gets a static, still-interactive figure: hover or tap to highlight, toggle between cases.

Name the motion's purpose before building it: **explanation** (how the process runs), **state indication** (what just changed), or **spatial consistency** (where this came from, where it went). Decoration has no place in a Lesson.

## Design rules

1. **Learner-paced.** The process is cut into discrete steps, and the learner advances them (step, back, reset). Each step stops and waits. Play is an optional extra and always has pause. People conceive of events as sequences of discrete steps, and learners who pace a segmented explanation themselves transfer it better.
2. **Predict, then reveal.** At least once per Visual, the learner commits to a prediction (the next state, which branch is taken, the output) before the Visual shows it, and the Visual says whether the prediction held.
3. **Change the input.** The learner edits the input or picks among cases. The presets are the exact examples from `sources/`, plus the boundary case and the case behind the most common misconception.
4. **Congruent.** What moves on screen corresponds to what changes in the concept, and only that moves. Every arrow, label and colour is true to the relation it shows.
5. **Persistent.** Animation is transient: the learner cannot reread a frame that has passed. After each step, the current state and the trace of earlier steps stay on screen, and the final state is a complete picture the learner can read at rest.
6. **Explained beside.** One caption line names what the current step did and why, placed next to the Visual and updated with each step. The words sit where the eyes already are, and arrive when the picture changes.
7. **One live signal.** A single "live" colour marks what is happening now. "Good" and "bad" colours mark outcomes. Everything else stays neutral, so attention lands where the step is. Colour always comes from the Notebook's theme tokens, so both themes work, and state is also written in text, never carried by colour alone.
8. **Up the ladder.** The Visual starts concrete (one case, one run) and lets the learner vary it until the general rule shows. The Lesson then asks for that rule in a `Recall`.
9. **Fits the hand.** It works at 400 px wide and in both themes: text legible, nothing cut off, controls reachable by thumb. Content wider than the screen scrolls inside its own container while the controls stay in view. Controls are labelled buttons that also work from the keyboard.

## Motion craft

These are the floor. When an animation skill is available, load it before writing motion; its rules govern where they go further.

- **Cheapest tool.** A CSS transition for a state you toggle with a class or attribute; Motion (`motion.dev`) for layout changes, exits, springs and drag.
- **Properties.** Animate `transform` and `opacity`. Entrances start from `scale(0.95)` and `opacity: 0`.
- **Curves.** `ease-out` for entering and exiting, `ease-in-out` for movement on screen, both as strong curves: `cubic-bezier(0.23, 1, 0.32, 1)` and `cubic-bezier(0.77, 0, 0.175, 1)`. Use the Notebook's motion tokens when they exist, and add new curves to them.
- **Duration.** A step's transition finishes before the learner's next click: 200–400 ms. Longer sequences run only after the learner pressed play.
- **Interruptible.** Steps fire rapidly, so they use transitions, which retarget from the current value. Clicking "next" mid-transition lands on the next state cleanly.
- **Reduced motion.** Under `prefers-reduced-motion`, every step still works: movement becomes an opacity change or an instant swap, and the trace and caption carry the change.
- **Touch.** Hover effects sit behind `@media (hover: hover) and (pointer: fine)`. Tap does everything hover does.

## Sources

- Bret Victor, [Explorable Explanations](https://worrydream.com/ExplorableExplanations/) (2011): active reading, explorable examples.
- C. D. Hundhausen, S. A. Douglas and J. T. Stasko, "A Meta-Study of Algorithm Visualization Effectiveness", _Journal of Visual Languages and Computing_ 13 (2002), 259–290: how learners engage with a visualization matters more than what it shows. T. L. Naps et al. (ITiCSE 2002 working group) turned this into an engagement taxonomy, from viewing through responding, changing and constructing.
- B. Tversky, J. B. Morrison and M. Bétrancourt, "Animation: can it facilitate?", _International Journal of Human-Computer Studies_ 57 (2002), 247–262: the congruence and apprehension principles, and interactivity as the remedy.
- T. N. Höffler and D. Leutner, "Instructional animation versus static pictures: A meta-analysis", _Learning and Instruction_ 17(6) (2007), 722–738: animations help most when they are representational, depicting the change to be learned.
- R. E. Mayer and P. Chandler, "When learning is just a click away", _Journal of Educational Psychology_ 93 (2001), 390–397: learner-paced segments improve transfer. Mayer's _Multimedia Learning_ gives the segmenting, signaling, coherence and contiguity principles.
- P. Ayres and F. Paas, "Making instructional animations more effective: a cognitive load approach", _Applied Cognitive Psychology_ 21(6) (2007), 695–700: the transient information effect.
- Motion craft follows [Emil Kowalski](https://emilkowal.ski)'s animation philosophy ([animations.dev](https://animations.dev)).
