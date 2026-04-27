# Final Project!
As per usual its the end of the semester busy time and I couldn't dedicate as much time as I wanted to this, but there are a few things I like about my final project

## Audio
I mostly just doodled on my own here, I had the idea of using the same note pattern and having it loop in on itself by going at different speeds and i used that to create the soft xylophone arp thing. I knew what drum machines I liked and made a simple beat from those, a lot of this was just spent mixing tbh. I would have liked to have things feel less repetitive but that would get rid of the initial idea of these overlapping arps, or at least heavily complicate it... besides it sounds fine enough. The bit I'm most proud of is the degradeBy variable I use to end the piece, its satisfying that they all follow the same rng so they pop in and out as a group. I was kinda trying to relax while making this and this was definitely born of that vibe, shout out to strudel's doccumentation it helps so much.

## Visual
I started with one of the boot up examples from hydra, from @naoto_hieda, I then tweaked the numbers and added my favorite thing, kaleid and rotation! Kaleidoscopes are just so satisfying to work with it pleases me greatly.

## Reflection
Honestly for the few hours I gave myself after realizing this was due a week earlier than I thought (my bad ofc), I'm pretty happy with the result!

# Le code
## Strudel
```
setcpm(100/4)
_$: n("<0 7 10 7 8 5 7>*4").scale("<g:major _ f:major _ c:major _ c:minor _ >").s("xylophone_soft_ff").trans(-12).adsr("0.4, 0, 1,1").room(0.4).gain(0.2)
_$: n("<0 7 10 7 8 5 7>*12").scale("<g:major _ f:major _ c:major _ c:minor _ >").s("xylophone_soft_pp").trans(12).adsr("0, 0.001, 0, 0.001").room(0.4).gain(0.1)
_$: n("<0 7 10 7 8 5 7>").scale("<g:major _ f:major _ c:major _ c:minor _ >").s("xylophone_soft_pp").trans(0).vib("16").vibmod("0.08").room(0.4).gain(1)
_$: n("<0 7 10 7 8 5 7>*2").scale("<g:major _ f:major _ c:major _ c:minor _ >").s("xylophone_soft_pp").trans(0).vib("16").vibmod("0.08").room(0.4).gain(0.8)

_$: n("<0 7 10 7 8 7 5 7>*4").scale("<g:major _ f:major _ c:major _ c:minor _ >").s("supersaw").trans(-12).adsr("0.4, 0, 1,1").room(0.4).gain(0.2).degradeBy(deg)

_$: n("<0 1 2 3 7>*16").scale("<g:major _ f:major _ c:major _ c:minor _ >").s("tri").trans(12).adsr("0, 0.001, 0, 0.001").vib("16").vibmod("0.2").room(0.4).gain(0.2).pan(sine).degradeBy(deg)

_$: s("bd - [- bd] -").bank("yamaharm50").gain(0.4)
_$: s("[- sd]!2").bank("rolandtr505").gain(0.6).degradeBy(deg)
_$: s("[- sd]!2").bank("rolandtr909").gain(0.6).degradeBy(deg)
_$: s("[- oh]!4").bank("rolandtr909").gain(0.1).room(0.3).degradeBy(deg)
_$: s("[hh - - hh] [- - hh -] [- - hh -] [ hh hh hh hh]").bank("yamaharm50").gain(0.2).pan(0.4).room(0.2).degradeBy(deg)

_$: n("[0 - - 0] [ - - 0 -] [ - - 0 -] [- - 0 - ]").scale("<g:major _ f:major _ c:major _ c:minor _ >").trans(-12).s("supersaw").distort(1.2).gain(0.1).degradeBy(deg)
_$: n("[0 - - 0] [ - - 0 -] [ - - 0 -] [- - 0 - ]").scale("<g:major _ f:major _ c:major _ c:minor _ >").trans(-12).s("tri").distort(1.3).gain(0.3)
```

## Hydra 

```
osc(20, 0.01, 0).color(0, 2, 2).rotate(1.57/4).out(o1)
osc(100, 0.01, 0).color(1, 0.2, 1).modulate(o1, 0).add(o1,1).modulatePixelate(o1,10,10).kaleid(4)
  .rotate(0.1,()=>Math.sin(time)* -0.0001)
  .kaleid(2)


 // .posterize(5)
  .scale(1)
  .out(o0)
```
