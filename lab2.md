# Lab Report 2 - Servers and SSH Keys (Week 3)

## Part 1
Chat Server Code: 
```import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String finalMessage = "";
    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("[=&]");
                if (parameters[0].equals("s")) {
                    String message = parameters[1];
                    String user = parameters[3];
                    finalMessage += 
                        String.format("%s: %s\n", user, message);
                    return finalMessage;
                }
                else {
                    return "404 Not Found!";
                }
        } 
        else {
            
            return "404 Not Found!";
        }
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
![lab2-1](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/a54290ca-315a-4047-a447-9c4a422fa97f)

![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/793acada-24ef-4f3e-b53e-996881960da9)



