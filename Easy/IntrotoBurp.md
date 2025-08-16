Open burpsuite browser, run instance on picoctf and open it on burpsuite browser, forward it from burpsuite.
Enter any random credentials into registration, then you get forwarded to the 2fa page.
On the first try, you enter any random otp and get to the invalid page.
**Here's the key idea after this point:**
Go back to the 2fa page, enter any random OTP again.
Intercept the request in burpsuite, remove the otp=\<num\> body text.
Forward the request.

You'll get your flag!