# My 1 Sample Project!
## What it is:
A trance tune inspired by those found in [SwitchAngel's most popular content](https://www.youtube.com/watch?v=HkgV_-nJOuE)
, Complete with drums, bass, pad and arps! All using the Shamisen general midi instrument.
## Process:
This was procrastinated until the last day but I had such a blast doing it I spent waayyyyy longer on it than I originally intended. The original sample i started making the instruments with was a banjo but I grew annoyed at its harmonics so I eventually switched to the shamisen. I first created a bass line, manipulating the decay to start short than expand. Next, I had synthesized basic kicks before and I searched up frequency envelope in the strudel learn tab and it was there! There was even a special curve made to suit kicks well so that came in super handy! The snare on the other hand took way longer and is still not ideal T-T. The concept is when i played the shamisen in the really low octaves you could hear the chaotic harmonics more than the fundamental, so by filtering out the fundamental and distorting the f out of it i could land on something that maybe sounds like a snare? It was kinda successful but such a pain to get sounding ok. I'm Super proud of the hats code tho! When working on the snare i noticed if i tuned the pitch envelope a certain way it sounded like a hat! The main adjustment after that point was adding a slight attack cuz the constant instant attack was starting to hurt my ears lol. Next i worked on the arpeggio, originally i had it mimicking the bassline but higher up and with more notes but it grew tiresome to my ears so i added a good bit of space and added the delay and cool .jux(press) spatialization thingamabob i found when searching the learn tab for panning settings as i was originally gonna have it move ear to ear but decided i like this more. Around here is when I took a break away from it to watch a couple of switchAngel's content when sharing what I was working on to some friends. I noticed here that there was a ducking function akin to sidechaining! I pretty much just nabbed that simple code she had and applied it to the kick, as well as putting each instrument in an orbit which should be called buses even tho they're not quite buses it just would make more sense to my brain. I also got distracted with the simple visualizers here they kept me company and motivated lol. I added chords to test out how they would sound now that i had more space for them with the ducking and after way too much trial and error (i had the kick ducking code duplicated on the bass by accident for the longest time),everything was implemented. Now this may seem simple but what followed was hours of tweaking numbers to get it to sound any good, it turns out the shamisen really doesn't want to be used for trance instruments who knew. (Oh also one of my fav fairly famous youtubers dougdoug posted a video about him learning strudel! It was very entertaining and it was super cool to see even more publicity for this niche ^-^). No AI was used in the making of this.
## Le Code
```
    setcpm(150/4)
    // kick
    _$:
    //note("e-1 ~ e-1 ~ ~ e-1 ~ e-1 ")
    note("c-1!4 ")
    .s("gm_shamisen").pdec(.1)
    .penv(30)
    .pcurve(1)
    .decay(.05)
    .sustain(0)
    .release(0)
    .compressor("-20:20:10:.1:.02")

      .gain(1.4)
     .duck("2:3:4").duckattack(.2).duckdepth(.8)

      .orbit(1)
       .color("purple")

    ._punchcard()
    ._spiral({ steady: .64 })
    // real bass
    _$:
    note("7!16")
    //note("7!2 13 4 14 4 7!2 7!2 13 ~4 4 14 4 21")

      .scale("<A:Minor _ C:Major G:Major>").sound("gm_shamisen").trans("<-36 _ -24 -36>")
    .coarse(30)
    .attack(0)
    .decay(0.1)
    .sustain(0)
    .release(0)

    .compressor("-20:20:10:.5:.02")
    .distort(1.7)
     .lpf(100)
      .gain(1.4)

     .orbit(4)

     .color("green")

    ._punchcard()
    ._spiral({ steady: .64 })
    // bass
    _$:
    note("7!2 4!2 11!2 4!2 9!2 4!2 6!2 4!2")
    //note("7!2 13 4 14 4 7!2 7!2 13 ~4 4 14 4 21")

      .scale("<A:Minor _ C:Major G:Major>").sound("gm_shamisen").trans("<-12 _ 0  -12>")

    .attack(0.01)
    .decay("<.06 .08 .1 .15>")
    .sustain(0)
    .release(0)
    .coarse(3)
    .gain(2)
    .room(0.3)

     .orbit(4)

     .color("red")

    ._punchcard()
    ._spiral({ steady: .64 })




    // snare
    _$:note("~ [b-1,b0] ~ [b-1,b0]")
    .s("gm_shamisen").pdec(.1)
    .penv(48)
    .pcurve(1)
    .attack(0.05)
    .decay(0.4)
    .sustain(0)
    .release(0)


    .distort(3)
      .coarse(14)
    .compressor("-10:20:10:.6:.02")
     .hpf(800)
        .bpf(2000)
      .bpq(1)
      .gain(0.8)
    .room(0.2)
     .color("orange")
    ._punchcard()
    ._spiral({ steady: .64 })
    //hh
    _$:note("[e-1 ~ e-1 e-1]!4")
    .s("gm_shamisen").pdec(.3)
    .penv(80)
    .pcurve(1)
    .attack(0.03)
    .decay(1)
    .compressor("-20:20:10:.5:.02")
    .hpf(1000)
    .crush(10)
    .distort(4)
    .hpf(10000)

     .color("cyan")
    ._punchcard()
    .gain(.05)

    ._spiral({ steady: .64 })

    //Arp
    _$:n("[7,14] ~ ~ [4,11] ~ ~ [9,16] ~ ~ [4,11] ~ ~ [7,14] [0,7] ~ [11,18]")
    .scale("<A:minor A:minor C:major G:major >").sound("gm_shamisen")

    .attack(0)

    .decay("<0.2 0.4 0.6 0.8 1 1.2 1.4 1.6 1.6 1.4  1.2 1 0.8 0.6 0.4 >")
    .sustain(0)
    .release(0)
      .distort("<0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.8 0.7 0.6 0.5 0.4 0.3 0.2 >")
    .crush(5)
    .gain(1)
    .jux(press)
    .delay(.5)


      .room(1.5)
    .orbit(3)
     .color("pink")
    ._punchcard()
    ._spiral({ steady: .64 })
    //PAD
    _$:n("[0, 2, 4, 7,9,11]")
    .scale("<A:minor A:minor C:major G:lydian >").sound("gm_shamisen").trans("<0 0 12 0>")
    .attack(0.04)
    .decay(0)
    .sustain(1)
    .release(0)
    .crush(5)
      .gain(0.5)
    .hpf(880)
    .phaser(2)
      .room(2)
    .orbit(2)
     .color("blue")
    ._punchcard()
    ._spiral({ steady: .64 })
```
