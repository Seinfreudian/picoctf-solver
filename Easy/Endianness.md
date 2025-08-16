Must know little endian and big endian.
Little Endian means a Right to Left read.
Big Endian means a Left to Right read.
I'm given a word: hhbej
they ask LE first:
so the R->L read is `jebhh`
convert it to Hex
That's your 1st answer
for BE:
use the normal L->R reead `hhbej`
convert to Hex
that's the 2nd answer
You get your flag!