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
