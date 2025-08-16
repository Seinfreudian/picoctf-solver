Did a reading of the CTF Hashing primer, did the exercise.
accessed the challenge url(nc). asked for the password compared to the hash.
installed Hashcat(already had it, thanks Kalie).
- Checking password characteristics match on any hashing website
-So just input the hash on the web, and you get the type identifier
for `482c811da5d5b4bc6d497ffa98491e38` you get `MD5`
for hashcat that is a `-m 0` or mode 0 since MD5 is mode 0
enter this sequence of hash onto a text file `hello.txt` 
On kalie there already exists a very dense and popular wordlist called rockyou and its at `/usr/share/wordlists/rockyou.txt.gz`
gunzip it
doesn't work normally with `gunzip` so use `sudo gunzip`
- Use hashcat to crack this hash
-`hashcat -m 0 -a 0 hello.txt /usr/share/wordlists/rockyou.txt
-a 0 is dictionary attack
-m 0 is MD5
<h6>Turns out, neither Hashcat OpenCL nor the background CPU or GPU work on my laptop, so we're <i>switching to JohntheRipper since it doesn't require any of these specs</i></h6>
`sudo apt install john`
`john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hello.txt`
we get the password `password123`

<h3>Part 2:</h3>
`Flag is yet to be revealed!! Crack this hash: b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3`
1. Put it in a hash identifier: Hash type: `b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3 - Possible algorithms: SHA1`
2. update the `hello.txt` file with `echo <hash>`
3. run it w john`<boiiiiieeeeee>`:`john --format=raw-sha1 --wordlist=/usr/share/wordlists/rockyou.txt hello.txt`
4. you get the password `letmein`

<h3>Part 3:</h3>
`Almost there!! Crack this hash: 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745`
1. Put it in hash identifier: `916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745 - Possible algorithms: SHA256` 
2. update `hello.txt` file with `echo <hash>`
3. run it with john: `john --format=raw-sha256`
4. you get the password `qwerty098`