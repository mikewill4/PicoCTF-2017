# The Vault
## Description
>There is a website running at http://2018shell.picoctf.com:53261 (link). Try to see if you can login!
## Solution
This challenge is a SQL injection. This is apparent when you see the php code
directly using user input in a SQL query. The one trick here is that the code
does check for SQL injections, but it only checks for them in the username. So
if you use something like this: anything' or 'x'='x for the password and
anything else for the username you should be able to login and get the flag.

Flag: picoCTF{w3lc0m3_t0_th3_vau1t_23495366}
