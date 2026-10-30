# Deutsch Sprint

Free mobile study kit for the Goethe-Zertifikat **A1** and **A2** — flashcards,
grammar, email writing, speaking simulation, listening and reading practice,
mock exams, and a 14-day blitz plan.

**Live:** https://de.gavv.in/

A dependency-free PWA: plain HTML, CSS, and vanilla JavaScript, no build step,
no framework, no bundler. Installable to a home screen and works offline after
first load.

## Run it locally

Any static server works, from the repository root:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening `index.html` via `file://` will not register the service worker.

## Structure

```text
index.html        single-page app shell, all screens as sections
css/style.css     all styling
js/app.js         entry point and routing
js/*.js           one module per exercise type (flashcards, lesen, hoeren, ...)
js/data/*.js      the learning content: word lists, prompts, texts, schedules
sw.js             cache-first service worker for offline support
manifest.json     PWA manifest
icons/, og.png    app icons and social preview image
```

## License

This repository is **dual-licensed by content type**, because the code and the
learning material are useful to different people under different terms.

| Part | Files | License | What it lets you do |
| --- | --- | --- | --- |
| **Software** | `index.html`, `css/`, `js/` (except `js/data/`), `sw.js`, `manifest.json` | [MIT](LICENSE) | Anything — reuse the app shell, engine, and UI in any project, including closed-source and commercial, with no obligation beyond keeping the copyright notice |
| **Content** | `js/data/` texts and exercises, translations and example sentences in the word lists, explanations, exam-style texts, UI prose, icons/artwork | [CC BY-SA 4.0](LICENSE-CONTENT) | Reuse and adapt freely, **but** you must credit the source and license your derivative content under the same terms |
| **Not licensed here** | the vocabulary *selection* in `words.js` / `words-a2.js` | Goethe-Institut's | Built against the official A1/A2 Wortliste; get the list from them, not from us (see [LICENSE-CONTENT](LICENSE-CONTENT)) |

Why the split:

- **Code** wants maximum reuse. MIT means someone can lift the flashcard engine
  or the offline PWA setup into their own app without asking, and it is
  compatible with virtually every other license.
- **Content** wants attribution and reciprocity. Exercise texts and word
  definitions are the labor-intensive part and the part most likely to be
  copied wholesale into a competing commercial product. CC BY-SA 4.0 keeps
  them open — including share-alike, so improvements stay open too.

The one thing that is *not* ours to license: the vocabulary list follows the
Goethe-Institut's published Wortliste, so only the translations and example
sentences we wrote are covered. See [NOTICE](NOTICE).

Nothing forces you to pick one; if you fork and only care about one half, comply
with whichever applies to the files you take.

### Attribution

For **code**, keep the copyright notice and MIT text (`LICENSE`).

For **content**, credit the project, link the license, and say what you changed:

> Learning content from "Deutsch Sprint" by Gavin D'souza,
> licensed under CC BY-SA 4.0 — changes were made.
> https://de.gavv.in/

A visible footer or "About" link in a fork is a good place for this.

### Trademarks and affiliation

"Goethe", "Goethe-Zertifikat", and "Start Deutsch" are trademarks of the
Goethe-Institut e.V. They are referenced descriptively to indicate which exam
format the exercises follow. This project is **unofficial** and is not
affiliated with, endorsed by, or sponsored by the Goethe-Institut or any other
examining body. Neither license grants trademark rights. See [NOTICE](NOTICE).

A fork must not imply it is this project or that the original author endorses
it, and must not present itself as an official study resource for any
certification.

### Third parties

No third-party libraries, fonts, or datasets are bundled.

One third-party request is made at runtime: a cookieless GoatCounter page-view
counter (`gc.zgo.at`, self-hosted endpoint, aggregate path only). No cookies,
no personal data, no cross-site tracking — delete the script tag in
`index.html` if you fork and don't want it. Everything else lives in
`localStorage` on your own device.

## Contributing

Contributions are accepted under the same split — code as MIT, learning content
as CC BY-SA 4.0. By opening a pull request you agree to license your
contribution accordingly. Content fixes (worse: a wrong article, a bad
translation) are as welcome as code changes.
