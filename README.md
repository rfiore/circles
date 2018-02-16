# Circles

I discovered a toy called ["Spirograph"](https://en.wikipedia.org/wiki/Spirograph). Was curious to implement something
similar in JavaScript, and this is my attempt after couple hours of work.

[![demo](https://i.imgur.com/PB5LJWv.gif)](https://anvaka.github.io/circles/)

## Math

I haven't checked all the math yet, please feel free to correct me if something
looks wrong.

Let's imagine we have a small circle with radius `r` inside a circle with radius `R`.
The inner circle center can be rotated according to

```
inner_cx = Math.cos(a) * (R - r)
inner_cy = Math.sin(a) * (R - r)
```

We want to figure out how much the inner circle has to be rotated, to cover
arc of the outer circle with angle `a` radians?

By definition of [a radian](https://en.wikipedia.org/wiki/Radian) the arc length
with angle `a` radians is equal to `s = R * a`. 

So, the inner circle must be rotated by some angle `b` and travel the same distance `s`.
Thus:

```
r * b = s
R * a = s   =>  r * b = R * a
            =>  b = (R/r) * a
```

And now we know our "unknown" inner rotation `b`. Circles are rotated in opposite
directions, so we need to add a minus sign to the final angle: 

```
b = -(R/r) * a
```

That's the math that I'm using in this [super short](https://github.com/anvaka/circles/blob/master/index.js) file. 

# License
MIT