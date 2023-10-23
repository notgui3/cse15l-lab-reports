# **Part 1** <br>

import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String serverString = "";
    int stringNum = 0;

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return serverString;
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    String addingString;

                    if(stringNum!=0){
                        stringNum++;
                        addingString = "\n" + stringNum + ". " + parameters[1];
                    }else{
                        stringNum++;
                        addingString = stringNum + ". " + parameters[1];
                        
                    }
            
                    serverString = serverString + addingString;
                    return serverString;
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}


![Image](stringserverss1.jpg)
![Image](stringserverss2.jpg)



# **Part 2**<br>



# **Part 3**
