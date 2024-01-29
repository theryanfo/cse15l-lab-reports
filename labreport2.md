# Lab Report 2
## The Code for ChatServer.java
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {

    String result = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(result);
        } 
        
        else if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            String message = parameters[1].split("&")[0];
            result += (parameters[2] + ": " + message + "\n");
            return String.format(result);
        } 
            return "404 Not Found!";
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
## Example Results
![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/75ba2ee4-3f87-4d8d-a9f2-fd9e5407b526)
- The handleRequest method is called with the argument: http://localhost:4000/add-message?s=Would%20you%20lose&user=Yuji
- The method then assigns the appropriate values to the temporary local variables 'parameters' and 'message'
- The class field 'result', which starts off as "", then has appended the user (Yuji) and their message (Would you lose) with proper formatting

![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/30d292d9-e095-4776-ac87-dff79eeb3218)
- The handleRequest method is called with the argument: http://localhost:4000/add-message?s=Nah,%20I%27d%20win&user=@thehonoredone
- The method then assigns the appropriate values to the temporary local variables 'parameters' and 'message'
- The class field 'result', which is currently "Yuji: Would you lose \n", then has appended the user (@thehonoredone) and their message (Nah, I'd win) with proper formatting
***

***
In lab, I learned
