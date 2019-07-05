# Logon
## Description
>I made a website so now you can log on to! I don't seem to have the admin password. See if you can't get to the flag. http://2018shell.picoctf.com:37861
## Solution
I went to the website and upon first inspection I was easily able to login as
admin, but I couldn't see the flag. I went into the developer tools and didn't
see anything in the JavaScript so I checked the Cookies under the application
tab. Turns out there was a cookie for admin with its value set to False. I
changed the value to True and refreshed the page. The flag was shown:
picoCTF{l0g1ns_ar3nt_r34l_a280e12c}
