# Infidex 176 V — Focusing Scale Generator

A drawing sheet for the [Infidex 176 V](https://identidem.design) focusing
helicoid that also generates the part it documents. Set the taking lens, turn
View A to check the marks fall where you expect, then export View B as an SVG,
print it at 100% and wrap it round the focus ring.

The two views are live: change the focus ring diameter and the Ø dimension
follows, change the rotation and the overall length does. Derived values are
shown in brackets, as reference dimensions are on a real drawing.

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
