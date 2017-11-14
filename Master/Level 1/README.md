# Master: Level 1
## Description: 
>I really need to login to this website, but the developer hasn't implemented login yet. Can you help?
## Solution:
I followed the link to the website and was presented with a text field and "Submit" button. My mind immediately went to SQL Injection, but after a few unsuccesful attempts with basic SQL injections, I decided to open up developer tools. The login functionaly is most likely JavaScript so I searched for any .js files in "Sources" and was able to find client.js:
***
    //Validate the password. TBD!
    function validate(pword){
    //TODO: Implement me
        return true;
    }

     //Make an ajax request to the server
     function make_ajax_req(input){
         var text_response;
         var http_req = new XMLHttpRequest();
         var params = "pword_valid=" + input.toString();
         http_req.open("POST", "login", true);
         http_req.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
  http_req.onreadystatechange = function() {//Call a function when the state changes.
  	    if(http_req.readyState == 4 && http_req.status == 200) {
                document.getElementById("res").innerHTML = http_req.responseText;
            }
        }
        http_req.send(params);
    }

    //Called when the user submits the password
    function process_password(){
        var pword = document.getElementById("password").value;
        var res = validate(pword);
        var server_res = make_ajax_req(res);
    }  
***
Bingo! Simply change "return false" to "return true", save, and click the submit button.
***
Therefore, flag is: `client_side_is_the_dark_sidea99c64effed2c2f1c9347eff536e949c`
