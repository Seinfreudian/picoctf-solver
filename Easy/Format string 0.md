I first did the `Breakf@st_Burger` input which kicked me out of the program. FIne, I did the second input then `Gr%114d_Cheese`.
Then for the 2nd prompt, I just had a divine spark of intuition pushing me to select `Cla%sic_Che%s%steak`. And turns out it was the right answer, since it likely caused a segfault error (probably a lot of % in the prompt) and gave me the flag!
TUrns out its a string format vulnerability check.

BUFSIZE is 32.
For the 1st prompt options are:
`char *menu1[3] = {"Breakf@st_Burger", "Gr%114d_Cheese", "Bac0n_D3luxe"};`
and the output or next function runs based on:
`else {
        `int count = printf(choice1);
        `if (count > 2 * BUFSIZE) {
          ``  serve_bob();
so when you pass 'Breakf@st_Burger' printf passes length of string into count so count=16,
2x32=63, count is NOT greater than 2\*buffsize  so it doesn't go to second prompt.

for 'Gr%114d_Cheese' printf reads '%114d' as 114 characters so it makes count=123, now 2\*buffsize is 2x32=64, since count is greater, it runs the function and takes us to the next prompt.

now we enter serve_bob():
the options for the 2nd prompt are:
`char *menu2[3] = {"Pe%to_Portobello", "$outhwest_Burger", "Cla%sic_Che%s%steak"};`

printf("%s", choice2) 
reads the string and "%s" in a string inputted leads to a string pointer, so in clas %s sic_Che(pointer) %s %s teak(pointer), in these specific addresses the flag is hidden so using an input like this rats it out.
Pe %s to_Portabello could potentially work, but it depends on the memory and pointer arrangement of the code, so can't really say.

basically the 1st input <i><b>leaks memory</b></i>. 
