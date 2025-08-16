Goal: provide address for win() function, win() is in the source code
run file vuln, shows the file details for the binary
`64-bit pie executable` PIE- randomized addresses
gdb vuln, to debug, even if main(), win() and segfault_handler have randomized addresses, it

**still follows a pattern to run the program
the difference between addresses remains constant**

to inspect it in assembly, run `disass main` or `disassemble main` - this gives the instruction address
1. the start address of main is then `133d`
2. `disass win` then the address is `12a7`
3. using a calculator take these hexadecimals and subtract to find the diff
4. `133d-12a7 = 96`
5. `nc rescued-float.picoctf.net 54393`
6. this gives the randomized address of main 
7. take that address - 96, gives win location
Done!

