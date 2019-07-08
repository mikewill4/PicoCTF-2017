# Irish Name Repo
# Description
>There is a website running at http://2018shell.picoctf.com:59464 (link). Do you think you can log us in? Try to see if you can login!
# Solution
If you navigate to the support page, you will notice a comment about SQL errors.
This gives away that this challenge involves a SQL injection on the admin login
page. By simplying googling for SQL injection examples, I was able to find one
that worked. Using "1' or '1' = '1" as the username and password dumped the
flag: picoCTF{con4n_r3411y_1snt_1r1sh_d121ca0b}
