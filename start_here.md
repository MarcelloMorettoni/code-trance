```
setCpm(136/4)
register('acidenv', (x, pat) => pat.lpf(100)
   .lpenv(x * 9).lps(.2).lpd(.12))

$: n("< 0 4 0 9 7>*16").scale("g:minor").trans(-12).o(3).s("sawtooth").acidenv(slider(0.719))._pianoroll()
$: n("<0>*16").scale("g:minor").trans(-24).detune(rand).o(4).s("supersaw").acidenv(slider(0.719))._pianoroll()
//$: s("bd:2*4").gain(1.1).lpf(5000)._scope()
$: s("bd:2!4").duck("3:4:5:6").duckdepth(.8).duckattack(.16)._scope()

```
