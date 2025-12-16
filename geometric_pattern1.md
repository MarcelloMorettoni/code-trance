```
setCpm(142/4)

// 1. The "Heartbeat" (Euclidean Kick)
// '3,8' plays the kick 3 times in 8 steps, distributed as evenly as possible.
$: s("bd:9(3,8)").gain(1.3).clip(1).shape(0.5)

// 2. The "Neural Network" (Generative Arp)
// This randomly selects notes from the C Minor scale and adds a tape-delay effect.
$: n("0 [2|3] . [7|5] [12|14]")
  .scale("c:minor").trans(12)
  .s("square").lpf(sine.range(400, 2000).slow(8)) // Filter breathes slowly
  .decay(0.1).sustain(0)
  .delay(0.5).delaytime(0.25).delayfeedback(0.6)
  ._pianoroll()

// 3. The "Data Stream" (Glitch Percussion)
// High-speed, randomized percussion to create texture.
$: s("glitch*8").n(irand(8))
  .pan(sine.range(0, 1).fast(2)) // Panning left to right quickly
  .hpf(1000).gain(0.8)

// 4. The "Subroutine" (Deep Bass)
// A heavy, detuned Reese bass grounding the track.
$: n("0").scale("c:minor").trans(-24)
  .s("sawtooth").detune(0.02)
  .lpf(200).gain(1.1)
```
