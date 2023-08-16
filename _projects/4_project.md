---
layout: page
title: riemapp
description:  a Python library for visualising complex mappings
img: assets/img/riemapp.jpg
importance: 4
category: work
---

riemapp is a fast, easy-to-use, minimal library for Python 3.7+ that aliases
[manim](https://github.com/ManimCommunity/manim) 0.16.0+ functions for
visualising animated and intuitive complex mappings (transformations from the
real plane to the complex plane) for various shapes and real-valued functions in
two dimensions. It uses a minimum number of dependencies through
[FFmpeg](https://github.com/FFmpeg/FFmpeg) and
[pangocairo](https://gitlab.gnome.org/GNOME/pango) on Linux.

[Github](https://github.com/Saransh-cpp/riemapp) & [Documentation](https://riemapp.readthedocs.io/en/latest/)

Users and learners may use riemapp to:

1. Plot (user-defined)
   - Points
   - Lines
   - Triangles
   - Squares
   - Rectangles
   - Other regular polygons
   - Circles
   - Irregular polygons
   - …and so on
2. Create smooth, precise animations for plotted figures and map them on the
   Argand plane according to user-defined complex functions.
3. Save these animations and play them in the default video player available

## Structure

- Right now, `riemapp` aliases the geometries provided by `manim` under
  `riemapp.geometry`. Users can either use these alias classes or directly use
  the `MObject`s provided by `manim`.
- `riemapp` programatically generates `manim` animations, and the code for this
  is available under `riemapp.core`. All of the information added by a user is
  passed into a placeholder class which inherits `manim.Scene`. This class'
  object is then used to render the animation.

## Usage example

```py
In [1]: import riemapp as rp
Manim Community v0.16.0.post0

In [2]: import numpy as np

In [3]: square = rp.geometry.Square(2.)

In [4]: square
Out[4]: Square(side_length=2.0) (alias for manim.Square)

In [5]: cm = rp.ComplexMap(square, lambda z: np.e ** z)

In [6]: cm
Out[6]: ComplexMap(f=Square(side_length=2.0) (alias for manim.Square), transformation=<lambda>)

In [7]: cm.generate_animation(run_time=2.)
Out[7]: Animate(f=Square(side_length=2.0) (alias for manim.Square), transformation=<lambda>)

In [8]: cm.render(preview=False)
```