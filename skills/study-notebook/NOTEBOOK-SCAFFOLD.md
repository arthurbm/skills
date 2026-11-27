# Notebook scaffold

The recipe for a workspace that has no Notebook yet: Fumadocs on Next.js, exported as a static site. It was extracted from one real Notebook built with Fumadocs 16, Next.js 16 and pnpm 11. Those tools move fast, so `--help` and the `AGENTS.md` the creator generates (it links the Fumadocs docs by task) are the source for flags, file names and APIs. This file keeps what they leave out: the order of the work, the gotchas and the reason behind each.

## Covered, and still to build

The source Notebook was a data-driven guide: one component per page, fed from a data module. Its scaffold is proven from creation to deploy: routes, sidebar, interface language, themes, browser state, build and publication. Four things the skill asks of a Notebook were outside it and are **still to build**:

- **The Block library** that [LESSON-STANDARDS.md](./LESSON-STANDARDS.md) names: `LessonHeader`, `Part`, `Steps`, `Callout`, `Book`, `Quiz`, `Recall`, `Decision`, `Next`. Step 7 gives the registry they plug into.
- **The page id** declared on each page, which keys the answers typed into Blocks. The store in step 6 takes whatever string key its caller passes; nothing yet declares one per page or checks that it is unique.
- **References**: the source Notebook had no Reference page.
- **Login for a private Notebook**: the source Notebook was public and kept out of search engines.

Before the work relies on one of these, tell the learner that it is new work with no tested recipe, and build it as part of the Lesson that needs it. Login is the exception: settle it with the learner before step 9 publishes anything meant to be private.

## Steps

Start from two answers the learner gives: the Notebook's title, and who may read it (anyone; anyone with the link, kept out of search engines; only people who log in).

1. **Create.** In the folder that will hold the Notebook, run the creator with the static Next.js template and no git of its own, since the workspace is the repository:

   ```sh
   pnpm dlx create-fumadocs-app --help
   pnpm dlx create-fumadocs-app <name> --template "+next+fuma-docs-mdx+static" --no-git --install --pm pnpm -y
   ```

   Read `--help` first and take the template name and flags from it. Then read the generated `AGENTS.md`.

   pnpm 11 refuses to run a dependency's install script until it is allowed, and esbuild has one: `pnpm install` ends with `ERR_PNPM_IGNORED_BUILDS`, and so does `pnpm exec next build`, which checks the install first. Allow it in `pnpm-workspace.yaml` at the Notebook's root, then install again:

   ```yaml
   allowBuilds:
     esbuild: true
   ```

   _Done when_ `pnpm install` exits 0 and `pnpm exec next build` is clean and writes `out/`.

2. **Serve the Notebook at the root.** The template puts a landing page at `/` and the pages under `/docs`; the Notebook has the plan at `/`.

   - Delete `app/(home)`.
   - Move the contents of `app/docs/` into a route group, such as `app/(notebook)/`, keeping the `[[...slug]]` folder.
   - Set the loader's `baseUrl` to `'/'` (the template reads it from `docsRoute` in `lib/shared.ts`).
   - Delete the `app/llms*` and `app/og` routes, unless the learner wants them, along with what feeds them: the `llms` export in `lib/source.ts`, the copy-as-Markdown buttons and the Open Graph image in the page component, and the placeholder GitHub links. The build's type check names each leftover, including the route strings that still say `/docs`.

   _Done when_ the route table printed by `pnpm exec next build` lists `/` and every page directly under it, and no `/docs`, `/llms*` or `/og` route.

3. **Plan and sidebar.** Pages live in `content/docs/`; `index.mdx` is `/`, so it is the plan: the ordered Lessons, done and next, with the upcoming ones that have no page yet as plain text. Replace the template's sample pages. Fix the sidebar order in `content/docs/meta.json` (`pages` array; the docs linked from `AGENTS.md` under "Organizing pages" give the syntax, including section separators). A list in MDX is enough for the plan; the source Notebook used a registered component that also read the browser state to mark what was done.

   _Done when_ `/` renders the plan and the built sidebar lists the pages in the plan's order.

4. **Language and indexing.** For a learner whose language is not English:

   - `lang` on `<html>` in `app/layout.tsx`.
   - `RootProvider` in `components/provider.tsx` takes `i18n={{ locale, translations }}`. The translation keys are the English phrases themselves, as the interface shows them: `'On this page'`, `'Search'`, `'Next Page'`. Collect them from the rendered interface: every English phrase still on screen is a missing key.
   - The static search index is built per language: set `language` in `app/api/search/route.ts` to the Orama name (`'portuguese'`).

   A Notebook kept out of search engines gets `robots: { index: false, follow: false }` in the root layout's `metadata` and a `public/robots.txt` that disallows everything. This hides a public URL from search; anyone with the link still reads it.

   _Done when_ the sidebar, table of contents, search dialog, theme switch and previous/next links show no English text, search finds a word from a page, and, for an unindexed Notebook, `out/index.html` contains `noindex`.

5. **State tokens.** In `app/global.css`, after the Fumadocs imports, define `--live`, `--good` and `--bad` under `:root` and again under `.dark`, the class the theme switch puts on `<html>`. Give each a background companion (`--live-bg`) when Blocks fill an area with a state. Components take colour from these tokens and from Fumadocs' own (`--color-fd-*`), so both themes follow from one definition.

   Third-party SVG inlined into a page brings its own `<style>`, and those rules are global: they restyle the rest of the page and ignore the theme. Strip that stylesheet and rewrite its rules under a class on the `<svg>`, with colours from the tokens.

   _Done when_ each of the three tokens has a value in both blocks, and step 8 finds each legible in its theme.

6. **Browser state.** One module (`lib/store.ts`) owns one `localStorage` key that holds one JSON object for the whole Notebook, and exposes it through a hook built on `useSyncExternalStore`.

   - The pages are static HTML, so the first render has no saved state. Pass the empty store as the server snapshot (the hook's third argument): the static HTML and hydration then agree, and the saved values appear right after mount.
   - Cache the parsed object in the module and replace it only on write: the snapshot function must return the same reference between writes, or React re-renders without end.
   - Wrap reading and writing in `try`/`catch`. Where storage is unavailable (some private windows), the state lasts while the page is open.
   - Put a version in the key (`<notebook>-v1`), so a later change of shape starts clean.
   - Add export to a JSON file and import from one. It is the only way the learner's answers leave that browser: to another device, or to the agent for review.

   _Done when_, with a component that writes to the store, a typed value survives a reload, export then clearing the site data then import restores it, and the browser console shows no hydration warning.

7. **Registry and README.** `getMDXComponents` in `components/mdx.tsx` is the MDX registry: a component added there is available in every `.mdx` page with no import. Give Blocks and the topic's Visuals a folder each under `components/`.

   The build is the page check. `next build` compiles every page, validates its frontmatter against the schema in `lib/source.ts`, type-checks and prerenders each route, and it fails on a component name that is missing from the registry. Topic invariants can join it: a data module that throws at import when its content is inconsistent fails the build the same way.

   Write the Notebook's README, since it is the source of truth later sessions read: how to run it, where pages, registry, Blocks, Visuals, tokens and store live, and the build and deploy commands.

   _Done when_ the README says where each item of "The Notebook" in `SKILL.md` lives, or that it is still to build, and a page that uses an unregistered component name fails `pnpm exec next build`.

8. **Check in a browser.** Build, serve `out/` (`pnpm start` in the template), and open it with a browser automation tool (such as `agent-browser`) at 400×860 and at 1300×900, in both themes.

   _Done when_, at both sizes and in both themes, nothing is cut off or illegible, the sidebar opens, search returns a page and saved state survives a reload.

9. **Deploy.** Only Vercel through its CLI was exercised. `out/` is a plain static site, so another static host is a reasonable choice, with its own gotchas to find.

   - Add `vercel.json` with `{"framework": "nextjs"}` before the first deploy. A project created from the CLI gets no framework preset, serves only `public/`, and answers 404 on every page.
   - Name the project in the command (`--project <name>`), so a deploy from any folder lands on the Notebook's own project; `vercel deploy --help` has the current flags. Put the full command in the README.
   - Vercel serves clean URLs: `public/x.html` answers at `/x` and 404s at `/x.html`. Link to a static file in `public/` by its clean URL.
   - Once a `.vercelignore` exists, the CLI stops reading `.gitignore`. That is how material that is generated and kept out of git (a third-party runtime under `public/`) gets uploaded; the file then has to exclude everything else itself: `node_modules`, `.next`, `out`, `.source`, `.env*.local`.

   _Done when_ `curl -s -o /dev/null -w '%{http_code}' <url>` answers 200 for `/` and for one inner page and 404 for a made-up path, and the URL and how access is protected are on the Notebook line of `NOTES.md`.
