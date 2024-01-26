# Lab Report 2 - Servers and SSH Keys (Week 3)

## Part 1
ChatServer.java Code: 

```
import java.io.IOException;
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

Screenshot 1:
![lab2-1](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/a54290ca-315a-4047-a447-9c4a422fa97f)
* `handleRequest()` was called.
* The relevant argument is `URI url` which has the value of `new URI("http://localhost:4000/add-message?s=Greetings&user=leoweng")`. The relevant field is `String finalMessage` which is initialized with the value `""`.
* `String finalMessage` takes the value `"leoweng: Greetings"` after this request.

Screenshot 2:
![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/793acada-24ef-4f3e-b53e-996881960da9)
* `handleRequest()` was called.
* The relevant argument is `URI url` which has the value of `new URI("http://localhost:4000/add-message?s=Goodbye&user=leoweng")`. The relevant field is `String finalMessage` which currently has the value `"leoweng: Greetings"`.
* `String finalMessage` takes the value `"leoweng: Greetings\nleoweng: Goodbye"` after this request.

## Part 2

Private Key Path: `C:\Users\leowe\.ssh\id_rsa.pub`
![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/dd759137-b064-4815-890d-6a517a8a673a)

Public Key Path: `~/.ssh/authorized_keys`
![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/ae1d9e22-0497-4c17-b5e7-396a3feee4b3)

Terminal Interaction, no password: 
![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/cf27df48-d56d-4eef-877c-7bd5dc836c64)

## Part 3
One main thing I learned from the last couple weeks was how to start a remote server that different people could access. I also learned more about SSH and how to save the keys so that you can log on without needing the type the password over and over. Finally, the week 3 lab made me more familiar with the differences between a bash terminal and the powershell terminal. 

