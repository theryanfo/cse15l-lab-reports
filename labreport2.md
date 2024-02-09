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
            String[] middle = parameters[1].split("&");
            if(parameters.length != 3 || middle.length != 2){
                return "404 Not Found!";
            }
            if(parameters[0].equals("s") && middle[1].equals("user")){
                result += (parameters[2] + ": " + middle[0] + "\n");
                return String.format(result);
            }
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

## Part 2

![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/b295f80b-4820-4964-b8f5-563977d70ecb)

![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/21b267c5-d313-4ec5-aefe-cb6f368c10ca)

![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/29dc894b-47a8-42f2-992b-7ad70a20b30c)

***

In lab, one thing I learned about URL structures and web servers. I learned about how URLs can have a domain, path, query, and fragment. I was also given an idea of the java code behind a possible web server, along with some code that changes the page based on the URL's path and query.
