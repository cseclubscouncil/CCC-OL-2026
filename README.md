# CCC Appointment Letters

Letters of appointment for the CSE Clubs Council, tenure 2026–27, and the page the team uses
to collect them: **type your five-digit VTU number → your letter appears → save as PDF**.

45 letters: council leadership (6), club heads and vice heads (28) and the social media team
(11). The President signs them, so there is no letter for the President.

| File | What it is |
| --- | --- |
| `index.html` | The whole thing — collection page and the letter. This is what you host. |
| `people.js` | The roster: VTU, name, role, club. Edit here to add or correct someone. |
| `logo-veltech.png`, `logo-ccc.png` | Crests used on the letter. |
| `president-signature.png` | The President's signature, cut out of the photo, transparent. |
| `President Sign.png` | The original photo, kept for reference. Not used by the page. |

## Hosting it

Upload the folder as-is (Vercel, Netlify, GitHub Pages — anything that serves static files)
and share the link. No build step, no server. `index.html` must sit next to `people.js` and
the three images.

Someone can also be sent straight to their letter: `…/index.html?vtu=30363`.

## How people use it

**On a computer:**

1. Open the link, type the five-digit VTU number, press **Find my letter**.
2. Their name and position appear, with the letter below.
3. **Download PDF** opens the print dialog — choose "Save as PDF".
   Best results: **A4**, **Portrait**, margins **None**, **Background graphics ON**.

**On a phone or tablet** the page shows a notice asking them to open it on a computer,
with a *Copy the link* button — phone browsers can't save the letter reliably. The check
looks at the browser and the pointer, not the window width, so a small desktop window still
works normally.

Only the letter prints; the page around it never does. An unknown number gives a plain
"we couldn't find it" message.

Each letter closes with a line pointing anyone who wants to check an appointment to the
council roster at **cse-ccc.vercel.app/team**.

## Changing the details

Everything that changes year to year sits in one `COUNCIL` block near the top of the
`<script>` in `index.html`:

```js
var COUNCIL = {
  tenure: "2026–27",
  issued: "20 September 2026",     // the date printed on every letter
  president: "Cheedella Venkata Sai Charan",
  signature: "president-signature.png",
  rosterUrl: "cse-ccc.vercel.app/team",
  ...
};
```

The wording is just below, in the `letter()` function — the appointment sentence adapts
itself to the three kinds of role:

- council — “…as **Vice President** of the **CSE Clubs Council**”
- club — “…as **Head** of the **Coding Club**, under the CSE Clubs Council”
- social media — “…as **Script Writer** on the **Social Media Team** of the CSE Clubs Council”

To add a person, copy a line in `people.js`. To swap the signature, replace
`president-signature.png` (transparent PNG, ink only). If that file is missing, the letter
prints a ruled signature line instead, so nothing breaks.

## Worth knowing

- **Everyone's name and VTU number is in `people.js`**, which anyone who opens the page can
  read, and any five-digit number can be tried. That is fine for an internal roster shared
  with the team, but treat the link as semi-public.
- **A letter can be altered after downloading** — that is true of any PDF, and no web page
  can prevent it. The council roster is the reference: if a letter and the roster disagree,
  the roster wins.
- **Names** are taken from the roster at cse-ccc.vercel.app/team and set in title case, with
  initials kept as initials (“B. Goutham”, “M S Adithya”).
- **Tenure 2026–27 and the issue date are assumptions** — change them in `COUNCIL` if the
  council records them differently.
- **Logo resolution** is modest (the crests are 213 px and 120 px wide). Fine on screen and
  on an office printer; get vector versions if these will be printed large.
