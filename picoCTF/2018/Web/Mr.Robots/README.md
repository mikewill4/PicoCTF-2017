# Mr.Robots
# Description
>Do you see the same things I see? The glimpses of the flag hidden away? http://2018shell.picoctf.com:15298
# Solution
This challenges hints at robots.txt, which is a file that tells robots what
parts of a web server they shouldn't visit. You can learn more about robots.txt
[here](https://www.robotstxt.org/robotstxt.html). For this challenge, you need
to add a "/robots.txt" to the url to look at the robots.txt file for the web
server. In the robots.txt, you will see that the web server is telling robots
not to visit /c4075.html. Simply add that to the original url and you get the
flag: picoCTF{th3_w0rld_1s_4_danger0us_pl4c3_3lli0t_c4075}
