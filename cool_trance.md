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
