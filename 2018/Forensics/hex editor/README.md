# hex editor
## Description
>This cat has a secret to teach you. You can also find the file in /problems/hex-editor_3_086632ac634f394afd301fb6a8dbadc6 on the shell server.
## Solution
This one is pretty simple. The challenge is called hex editor, so let's take a
look at the hex of hex_editor.jpg.
***
    $ xxd hex_editor.jpg | grep pico
    00012940: 3a20 2270 6963 6f43 5446 7b61 6e64 5f74  : "picoCTF{and_t
***
As you can see we got a piece of the flag. Now we can use the -A option for grep
to display more lines after the match to get the entire flag.
***
    $ xxd hex_editor.jpg | grep -A 3 pico
    00012940: 3a20 2270 6963 6f43 5446 7b61 6e64 5f74  : "picoCTF{and_t
    00012950: 6861 7473 5f68 6f77 5f75 5f65 6469 745f  hats_how_u_edit_
    00012960: 6865 785f 6b69 7474 6f73 5f38 4263 4136  hex_kittos_8BcA6
    00012970: 3761 327d 220a                           7a2}".
***
Flag: picoCTF{and_thats_how_u_edit_hex_kittos_8BcA67a2}
