# Buttons
## Description
>There is a website running at http://2018shell.picoctf.com:44730 (link). Try to see if you can push their buttons.
## Solution
If you compare the requests made by button1.php and button2.php in the Network
tab of Developer tools, you will see that button1.php makes a POST request,
while button2.php makes a get request. In order to get the flag, all we have to
do is make a POST request to http://2018shell.picoctf.com:44730/button2.php.
This can easily be done via curl.
***
    $ curl -i -X POST http://2018shell.picoctf.com:44730/button2.php
    HTTP/1.1 200 OK
    Content-type: text/html; charset=UTF-8

    Well done, your flag is: picoCTF{button_button_whose_got_the_button_dfe8b73c}
***
