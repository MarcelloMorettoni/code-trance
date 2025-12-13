` ` `
setCpm(136/4)
register('acidenv', (x, pat) => pat.lpf(100)
   .lpenv(x * 9).lps(.2).lpd(.12))

$: n("< 0 4 0 9 7>*16").scale("g:minor").trans(-24).detune(rand).o(4).s("sawtooth").acidenv(slider(0.542))._pianoroll()

$: s("bd:2!4")._scope()
` ` `
