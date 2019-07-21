# Client Side is Still Bad
## Description
>I forgot my password again, but this time there doesn't seem to be a reset, can you help me? http://2018shell.picoctf.com:55790
## Solution
Similar to the first web challenge, this challenge just involves inspect
element. By looking at the HTML you can see the form for the credentials calls a
JavaScript method called verify(). Switching to the sources tab you can see the
JavaScript.
***
    <script type="text/javascript">
        function verify() {
            checkpass = document.getElementById("pass").value;
            split = 4;
            if (checkpass.substring(split*7, split*8) == '}') {
              if (checkpass.substring(split*6, split*7) == 'd366') {
                if (checkpass.substring(split*5, split*6) == 'd_3b') {
                 if (checkpass.substring(split*4, split*5) == 's_ba') {
                  if (checkpass.substring(split*3, split*4) == 'nt_i') {
                    if (checkpass.substring(split*2, split*3) == 'clie') {
                      if (checkpass.substring(split, split*2) == 'CTF{') {
                        if (checkpass.substring(0,split) == 'pico') {
                          alert("You got the flag!")
                          }
                        }
                      }
              
                    }
                  }
                }
              }
            }
            else {
              alert("Incorrect password");
            }
          }
    </script>
***
The flag is clearly in the JavaScript.

