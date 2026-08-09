# The Mentor Playbook

Slides for a conference talk on how to mentor well — what mentoring actually
is, who to mentor, how to respond, and why it's worth doing.

**[View the deck →](https://gabidombrowski.github.io/the_mentor_playbook/)**

## The talk

> We often find ourselves in situations where we have to knowledge share and
> mentor others, but we often don't take the time to learn _how_ to be better
> mentors. So are we doing it right? Through my work as Mentor Director for a
> monthly coding class, I've been able to compile effective methods through
> research and experience that will help all developers be better mentors,
> whether within an established mentor/mentee relationship or quick day-to-day
> teaching opportunities. By being thoughtful and deliberate in mentoring
> moments, even sometimes in counterintuitive ways, we can all be a part of
> creating richer tech communities that foster inclusivity and thrive on
> collective growth.

Presented at CodeMash 2020, NDC Porto 2020, Code PaLOUsa 2020, and
ThunderPlains 2019.

Recordings:
[NDC Porto 2020](https://www.youtube.com/watch?v=AsT4bCM4tJc) ·
[ThunderPlains 2019](https://www.youtube.com/watch?v=ondACXEEqlw)

The talk grew out of the
[Mentor Playbook](https://github.com/KansasCityWomeninTechnology/MentorPlaybook)
written for Coding & Cocktails, a program of Kansas City Women in Technology.

## Running it locally

```bash
npm install && npm start
```

Then open <http://localhost:8000>. No build step — `index.html` is the deck.

### While presenting

| Key            | Does                                              |
| -------------- | ------------------------------------------------- |
| `→` / `Space`  | Next slide or fragment                            |
| `←`            | Back                                              |
| `S`            | Speaker view — notes, timer, and next-slide preview |
| `Esc` / `O`    | Slide overview                                    |
| `F`            | Fullscreen                                        |
| `B`            | Blank the screen                                  |

Nearly every slide has speaker notes in an `<aside class="notes">`, so `S` is
the one worth remembering.

### Exporting a PDF

Open <http://localhost:8000/?print-pdf> and print to PDF from the browser
(landscape, background graphics on, margins none).

## Layout

```
index.html        the whole deck — one <section> per slide
css/custom.css    the theme: palette, type, slide layouts, photo backgrounds
images/           slide photography and the QR code
dist/, plugin/    vendored reveal.js 5 — do not hand-edit, see below
```

### Adding a slide

Slides are plain HTML sections. The common shapes:

```html
<!-- A section break over a full-bleed photo -->
<section class="topic img NAME">
  <div class="title-wrapper"><h2 class="title">Section title</h2></div>
</section>

<!-- A content slide, one idea revealed at a time -->
<section>
  <div class="title-wrapper"><h2 class="title subtitle">Slide title</h2></div>
  <div class="content">
    <p class="fragment">First point</p>
    <p class="fragment">Second point</p>
  </div>
  <aside class="notes">
    <p>What to say here.</p>
  </aside>
</section>
```

Use `class="content single"` instead of `content` when the slide carries a
single line rather than a list.

For a photo slide, drop the image in `images/` and add one line to the photo
block in `css/custom.css`:

```css
.img.NAME {
  --slide-image: url(../images/NAME.jpg);
  --slide-image-y: center; /* optional: top (default), center, bottom */
}
```

The shared tint and opacity are applied for you.

### Updating reveal.js

`dist/` and `plugin/` are copied out of the npm package and committed so the
deck stays a static site that GitHub Pages can serve and that works offline.
To move to a newer reveal.js:

```bash
npm install reveal.js@latest && npm run sync-reveal
```

Then click through the deck before committing — reveal's layout defaults have
shifted between majors before.

## Accessibility notes

Worth preserving if you edit the theme:

- Slide titles are real `<h1>`/`<h2>` elements, not styled paragraphs.
- The palette in `css/custom.css` is tuned so text clears WCAG contrast
  minimums against the page gradient. Lightening `--teal` or `--pink` will
  break that; the comment there records the numbers.
- The Stages of Competence diagram is a CSS background, so it carries a
  `.visually-hidden` text alternative in the markup.

## Credits

Slides by [Gabriela Dombrowski](https://digitallotusdev.com), licensed
[CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/).

Built with [reveal.js](https://revealjs.com) (MIT). Slide photography is from
film and television, used for commentary and illustration.

The "Ask for feedback" slide uses a 1966 NBC publicity photo of Leonard Nimoy
as Spock — public domain (published without a copyright notice), via
[Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Leonard_Nimoy_Spock_1966.JPG).
