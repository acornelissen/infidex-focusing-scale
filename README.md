# Infidex 176 V — Focusing Scale Generator

A generator for the focusing scale strip on the
[Infidex 176 V](https://timetowaste.ru/en_infidex) helicoid. The strip is drawn
against a millimetre rule so you can read its real length at a glance, the focus
ring can be turned to check the marks land where you expect, and the export is a
1:1 SVG ready to print and wrap.

Derived values are shown in brackets, as reference dimensions are on a real
drawing.

## Running it

It is one static page with no build step. Open `index.html`, or serve the
directory with anything:

```
python3 -m http.server
```

## Where the numbers come from

The helicoid figures were measured off the printed parts rather than assumed:

| | |
|---|---|
| Thread lead | 5.0005 mm per turn, single start |
| Focus ring diameter | 61.00 mm |
| Grip band height | 13.5 mm |

The lead was taken by cross-correlating the focus ring's bore profile between
heights: the profile rotates −71.99°/mm and repeats with exactly 0.00° of
rotation at Δz = 5.00 mm.

Extension follows from rotation, `extension = lead × rotation / 360`, and the
subject distance from the thin-lens relation `e = f² / (u − f)`. At the default
340° that gives ∞ to 1.44 m with the 80 mm lens, or ∞ to 0.70 m with the 55 mm.

The two inner rings in the Infidex STL set — 41.70 mm for the 55 mm lens, 36.10 mm
for the 80 mm — position each lens so infinity still lands, so focal length is the
only thing that changes between the two builds.

## Gerber output

The Gerber button produces a zip of the same scale as a flexible PCB, which
gives you a far more durable strip than paper: white silkscreen on black
coverlay is exactly the artefact.

Order it as **1 layer, flexible, black coverlay, white silkscreen**. The set is
one layer only so the fab's parser doesn't read it as two.

| File | |
|---|---|
| `.GTL` | copper, a plain pour inset 0.5 mm from the edge |
| `.GTS` | soldermask, deliberately empty |
| `.GTO` | silkscreen, the scale itself |
| `.GKO` | board outline |
| `.DRL` | drill, no holes |
| `Bottom Stiffener.GBR` | where the 3M468 adhesive goes |

If you take the 3M468 tape option under Stiffener, JLC need the stiffener *area*
as well as the order option — selecting one without the other gets the file
queried. That layer marks the whole back face, inset 0.3 mm so it cannot
overhang after routing. There is no standard extension for a stiffener layer, so
the filename says what it is, since a person reads it. Order without the tape and
you should delete that file.

The empty soldermask layer is the trick: Gerber's mask layer defines *openings*,
not coverage, so an empty one means the coverlay covers everything.

The copper does nothing electrically. It is there so the fab builds a normal
flex stack rather than laminating coverlay onto bare polyimide, which their
checks may query. It bends fine at a 30 mm radius for a one-time install.

Gerber has no text primitive, so the numerals are drawn as single-stroke
polylines at 0.22 mm — above JLCPCB's 0.15 mm silkscreen minimum, and the 2.3 mm
cap height clears their 0.8 mm text minimum comfortably. The ∞ is a Gerono
lemniscate rather than hand-plotted points.

On the SVG the ∞ and the `m` sit on their index bars with a black halo behind
them. Silkscreen has no black ink, so on the PCB they are shifted clear of the
bars instead.

## Before you cut

Infinity is assumed to sit at the zero-rotation stop. Check it on ground glass
first. If the helicoid racks in past infinity, put the residual extension in the
"Extension at infinity" field and the whole scale shifts to match.

Keep the strip height at or under 13.5 mm — that is the smooth band on the focus
ring, measured from where the flutes sit on the ribbed variant of the part.

## Licences

Page © Albert Cornelissen / IDENTIDEM.design.

Saira Semi Condensed and Azeret Mono are subset and self-hosted under the SIL
Open Font License 1.1; the licence texts are in `assets/fonts/`.

## Credits

The camera is [Infidex 176 V](https://timetowaste.ru/en_infidex), an open source
3D printed panoramic film camera by Time to Waste.

The scale arithmetic follows [Parametric Focusing Scale for 17–31 mm, M65 and
M77](https://www.printables.com/model/1610905-parametric-focusing-scale-for-17-31-mm-m65-and-m77)
on Printables, adapted here for the Infidex helicoid.
