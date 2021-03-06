# Getting Started

CubicBezier aims to replicate the CubicBezier timing function found
in CSS used with the animation-timing-function property and the 
transition-timing-function property. 

A Cubic Bezier curve is defined by four points `p0`, `p1`, `p2`, and `p3`.
`P0` and `P3` are the start and the end of the curve and, in CSS these 
points are fixed as the coordinates are ratios. `p0` is (`0`, `0`) and 
represents the initial time and the initial state, `p3` is (`1`, `1`) 
and represents the final time and the final state.

Since time (`x`) is always between `0` and `1`, it is useful to treat 
time and state as percentages. Where `x` is the percentage of time 
that has elapsed in your animation / transition, and `y` is the 
percentage of change between your object(s) start and end states.


## Why?

Let's say you want to "tween" (animate / transition) an object's position.
You might take the travel distance, and divide by the steps ("frames")
of your tween. On every frame, you'd increment the object's position.
This would be the equivelant of a linear Cubic Bezier; and it tends 
to look / feel very unnatural. To make the movement feel more natural,
you'd use an "easing equation" (eg. `CubicBezier.solve(x, :ease_out_quad)`). 
To further make the animation feel more natural, you'd want to compute 
the object's position about 60 times per second (60 fps). This will smooth 
out the position changes to make it feel more fluid. 
The combination results in natural and fluid tweens!


## Syntax

You can use atoms to represent common easing equatons, or pass a control 
point tuple. The examples below are equivelant:

```elixir
iex> CubicBezier.solve(0.25, :ease_out_quad)
iex> CubicBezier.solve(0.25, {0.250,  0.460,  0.450,  0.940})
```

This will return a `y` state of ~`0.45`, given an `x` time of `0.25`. 

> Ease-Out-Quad is fast at first, and slow towards the end.


## Reference

* Easing function examples: https://easings.net/en
