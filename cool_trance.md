```
setCpm(144/4)

// Custom Acid Register (optional but cool)
//register('acidenv', (amt, pat) => pat.lpf(100).lpenv(amt).lpq(10))

register('acidenv', (x, pat) => pat.lpf(100).lpenv(x * 9).lps(.2).lpd(.12))
register('trancegate', (density, seed, length, x) => {
  return x.struct(rand.mul(density).round().seg(16).rib(seed, length)).fill().clip(.7)
})

register('rlpf', (x, pat) => { return pat.lpf(pure(x).mul(12).pow(4)) })

$: n("<3@3 4 5 @3 6>*2".add("-14,-21")).scale("g:minor").s("supersaw").lpenv(2)
//$: n("0".add(-14)).scale("g:minor").s("supersaw").o("2").lpenv(2)
$: s("hh:1/2").fit().o(5)._scope()
$: s("bd:2!4").duck("3:4:5:6").duckdepth(.8).duckattack(.16)._scope()
$: n("0@2 <-7 [-5 -2]>@3 <0 -3 2 1>@3".add(7).add("<5 4 0 <0 2>>")).scale("g:minor").s("supersaw").o(3).delay(2).pan(rand).rlpf(slider(0.931)).lpenv(2)._pianoroll()
```

OR

```
setCpm(144/4);

// -----------------------------------------------------------------------------
// HELPER REGISTERS
// -----------------------------------------------------------------------------

// Custom Acid Envelope
register('acidenv', (x, pat) => 
  pat.lpf(100)
     .lpenv(x * 9)
     .lps(.2)
     .lpd(.12)
);

// Trancegate Effect
register('trancegate', (density, seed, length, x) => {
  return x.struct(
    rand.mul(density)
        .round()
        .seg(16)
        .rib(seed, length)
  ).fill().clip(.7)
});

// Resonant Low Pass Filter Helper
register('rlpf', (x, pat) => { 
  return pat.lpf(pure(x).mul(12).pow(4)) 
});


// -----------------------------------------------------------------------------
// DRUM TESTS (Commented Out)
// -----------------------------------------------------------------------------

/* // TEST 1: The "Classic Trance" Kick
$: s("909bd!4")
   .shape(0.5)        // Saturation
   .hpf(30)           // Clean sub
   .lpf(8000)         // Remove fizz
   .gain(1.2)
   ._scope()
*/

/* // TEST 2: The "Hard" Kick
$: s("bd:8!4")
   .shape(0.1)        // Heavy saturation
   .lpq(2).lpf(2000)  // Resonant Thud
   .clip(1)
   ._scope()
*/

/* // TEST 3: The Layered Kick
$: stack(
  s("bd:2!4").shape(0.6).lpf(500),    // Thud
  s("bd:2!4").hpf(1000).gain(0.8)     // Click
)._scope() 
*/


// -----------------------------------------------------------------------------
// ACTIVE PATTERNS
// -----------------------------------------------------------------------------

// 1. Chords / Pad layer
$: n("<3@3 4 5 @3 6>*2".add("-14,-21"))
   .scale("g:minor")
   .s("supersaw")
   .lpenv(2)

// 2. High Hats (Commented)
// $: s("hh:1/2").fit().o(5)._scope()

// 3. Main Kick
$: s("bd:2!4")
   .shape(0.2)
   .lpf(500)
   .cutoff(3000)
   .duck("3:4:5:6")
   .duckdepth(.8)
   .duckattack(.16)
   ._scope()

// 4. Lead Melody (The complex cipher node)
$: n("0@2 <-7 [-5 -2]>@3 <0 -3 2 1>@3".add(7).add("<5 4 0 <0 2>>"))
   .scale("g:minor")
   .s("supersaw")
   .o(3)
   .delay(2)
   .pan(rand)
   .rlpf(slider(0.931))
   .lpenv(2)
   ._pianoroll()

```
