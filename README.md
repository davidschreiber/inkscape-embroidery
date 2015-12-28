Inkscape is a natural tool for designing embroidery patterns. The only challenge is converting the Inkscape design to a stitch file. Here's a rough cut as such a tool that got me through my first project. It may work for you, or maybe you can fix a bug or two and make it more robust for your application.

## Installation.

1. Download the distribution from here (e.g. via `git clone`)
2. Install shapely (http://trac.gispython.org/lab/wiki/Shapely) Python bindings to the GEOS library.
3. Place or link `embroider.{inx,py}` into `${HOME}/.config/inkscape/extensions`.

## Usage

Create a drawing in Inkscape made of filled regions.
Select the regions you want to export as a stitch file.
Ungroup repeatedly until there are no groups left,
and convert objects to paths.
(Embroider doesn't know how to handle text or rectangle objects;
they must be converted down to paths before it can work with them.
I don't know how to call "back into" Inkscape to do this automatically.)
Select the `Extensions -> Render -> Embroider`.

If it works (and it very well might!), you'll get a new grouped object
showing the proposed stitching path. It may be easy to miss, since the
new strokes appear in the same color as the underlying fill. (If you
forgot the "ungroup" step, it may also appear at a random place on
your canvas.)

As a side effect, Embroider also creates a file in Inkscape's current
directory called embroider-output.exp.
If you like the stitch pattern you see, then open that output file
in a converter program and save it to the appropriate format for
your machine.

(I use Wilcom's TrueSizer, available as free-as-in-beerware,
inside WINE to convert my output to Brother .PES format.)

