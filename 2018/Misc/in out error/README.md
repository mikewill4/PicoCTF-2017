# in out error
## Description
>Can you utlize stdin, stdout, and stderr to get the flag from this
>[program](https://2018shell.picoctf.com/static/0d4867de7f7e5757410f23bfa00a6aae/in-out-error)? You can also find it in /problems/in-out-error_1_24ebc7186086f0f9a710de008628c561 on the shell server
## Solution
As hinted by the description, this challenge has to do with stdin, stdout, and
stderr. The program prompts you for input, which is stdin. When you provide the
correct input you get a jumbled mess of output, but the flag appears to be in
there somewhere. Turns out the program is returning both the stdout and stderr
output mashed together.

I initially tried to pipe the stderr somewhere else like so:
***
    $ ./in-out-error 2>/dev/null
***
2 is the file descriptor for stderr, but this gave me song lyrics as output.
That meant that the flag must be in stderr, so I piped it to a file.
***
    $ touch ~/flag.txt
    $ ./in-out-error 2>~/flag.txt
    $ cat flag.txt
    picoCTF{p1p1ng_1S_4_7h1ng_7b9360ca}
***
