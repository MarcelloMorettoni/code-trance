` ` `
// The Golden Ratio Song
// BPM is 144 (A Fibonacci number: 12th in the sequence)
setCpm(144/4)

// 1. THE SPIRAL BASS (Intervals)
// Uses degrees 0, 3, 5, 8 (Fibonacci numbers)
// It climbs up, mimicking the expansion of a spiral.
$: n("<0 3 5 8>").scale("d:minor").trans(-24)
   .s("triangle").lpf(300).gain(1.2)
   .clip(1).shape(0.6)

$: s("hh*8").struct("t(5,8)")
   .gain(0.8).hpf(5000)

// Corrected Phi Polimeter
$: n("0 1 1 2 3 5 8 13 8 5 3 2 1")
   .scale("d:minor").trans(12)
   .s("sine")
   .attack(0.01).release(0.3) // Replaced .env/.rel with .attack/.release
   .delay(0.5).delaytime(8/13)
   ._pianoroll()
` ` `
