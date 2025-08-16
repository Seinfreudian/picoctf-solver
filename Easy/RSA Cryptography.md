It works by factoring large numbers(finding primes). Uses 2 keys- public, private. Public for encryption, private for decryption.
Crux of security: very difficult to factor/find primes of VERY large numbers(So don't repeat the primes or numbers)

<b>Good for</b>: files, email, application
<b>Bad for</b>: large files because it's then resource heavy(makes a VERY big number) and less-efficient than symmetric key encryption

"A user of RSA Cryptography creates and then publishes the product of two large prime numbers, along with an auxiliary value, as their public key. <i>The prime factors must be kept secret.</i> <b>Anyone can use the public key to encrypt a message, but only someone with knowledge of the prime factors can feasibly decode the message.</b>"

Steps:
1. Let's say there's a message 'Hello girl' 
2. Convert it to a number
3. Convert number to an encryption key <i>e</e> and a modulus <i>N</i> such that <i><b>C = m^e mod N</i></b> where <i>C</i> is the ciphertext
4. C is transferred to the other person and decrypted using the key <i>d</i> and <i>N such that m= C^d mod N</i> 
5. Python uses pycryptodome to convert message to integers(step 2)

N=p\*q
N is a very large number, p and q are very large primes
since p,q are primes -> they are odd numbers -> N is odd
<i>2 is the only even prime and since p,q are very large primes, they can't be even</i>

***Euler's Totient Function*** - helps create matching function to ensure the use of correct private key to decrypt public key messages

<h3>Problem:</h3>
`nc verbal-sleep.picoctf.net 51510`
on running this continuously, we observe that the N is even rather than odd -> one of the p or q is even -> not a prime!!!!!

on doing:
`from Crypto.Util.number import long_to_bytes
`n=19578211866095794991700378896307915690562370343073988627328334770338184846535377788394349831667536202848430588852821908607566530423018072356460408665347358
`x=n//2
`print(x)`

on doing this, we get x as an odd number. Which means `N=p*q` means p=2 and q=N/2
`N=2*N/2`
Using tolentie eqn: `phi_n=(2-1)*(q-1)=q-1`
`d=pow(e,-1,phi_n)`
`m=pow(c,d,n)`
you get the flag

<h3>OR</h3>
just go to RSA Cipher decode, enter your d, e, n, c and you'll get your flag!!!

`
