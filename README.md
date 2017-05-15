svg-intersections
=================

A library of intersection algorithms covering all SVG shape types.
Possible to intersect rotated/scaled/skewed shapes.


Installation
-------

To install the original, run

    npm install svg-intersections

If you would like to use this version instead, I haven't uploaded it yet so
you'll have to add this repo to your `package.json`:

```
"dependencies": {
  "svg-intersections": "https://github.com/nicolassatragno/svg-intersections"
}
```

API
---

This module exports two functions:

The `intersect` function takes two shapes as an input an returns an result
object providing a result status, and all intersection points of the two shapes.

```intersect (shape1, shape2)```


The `shape` function wraps the necessary input parameters for each of
the two shapes. It requires the SVG element name of the shape as a string
and an object of the SVG element's attributes.

```shape (svgElementName, svgAttributes)```


Usage example
-------------

**Example 1:**

![Example image](./images/UsageExample1.png)

```javascript

    var svgIntersections = require('svg-intersections');
    var intersect = svgIntersections.intersect;
    var shape = svgIntersections.shape;

    var intersections = intersect(
        shape("circle", { cx: 0, cy: 0, r: 50 }),
        shape("rect", { x: 0, y: 0, width: 60, height: 30 })
    );

```

Changes from the original
-------------------------

* Do not use `instanceOf` to check for transformation matrices. This was
  breaking the library integration with when used with a different Matrix2D
  prototype instance.

* Add support for h, H, v and V path segments.

Credits
-------

The implementation is based on the intersection procedures by Kevin Lindsey
([http://www.kevlindev.com](www.kevlindev.com)) with contributions by
Robert Benko ([http://www.quazistax.com](www.quazistax.com)).

Cloned from [Signavio](https://github.com/signavio/svg-intersections) because
the repo does not have issues enabled and I needed to do some changes to suit
the library to my needs.
