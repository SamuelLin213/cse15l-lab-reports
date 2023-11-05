# Lab Report 2: Servers and SSH Keys (Week 3)

## Part 1

`/add-message?s=Hello`<br />
![Image](./report2/add-message1.png)  
1. The `main()`, `handleRequest()` and `getList()` methods are called.  
2. `main()` takes in an array of strings, `handleRequest()` takes in a URI and `getList()` doesn't have any parameters. Additionally, there's a string `ArrayList` in the `Handler` class.  
3. The `ArrayList` changes from this request, with "Hello" stored in the first element.  

`/add-message?s=How are you`<br />
![Image](./report2/add-message2.png)  
1. The `main()`, `handleRequest()` and `getList()` methods are called.  
2. `main()` takes in an array of strings, `handleRequest()` takes in a URI and `getList()` doesn't have any parameters. Additionally, there's a string `ArrayList` in the `Handler` class.  
3. The `ArrayList` changes from this request, with "How are you" being stored in the second element.  

### Code for `StringServer`
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> strings = new ArrayList<String>(); // create new list for strings

    public String getList()
    {
      String res = "";
      int cnt = 1;

      for(String s: strings)
      {
        res += Integer.toString(cnt++) + ". " + s + "\n";
      }
      return String.format(res);
    }

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message"))
        {
          String[] parameters = url.getQuery().split("=");
          if (parameters[0].equals("s"))
          {
              String temp = parameters[1];
              strings.add(temp); // add string to list
              return getList();
          }
        }
      return "404 Not Found!";
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
```

## Part 2

Path to private key: <br />
![Image](./report2/privateKey.png) <br />
Path to public key: <br />
![Image](./report2/publicKey.png) <br />
Login without password: <br />
![Image](./report2/login.png) <br />   


## Part 3
Something I learned in week 2 and 3 was how to launch a server and specify which port to launch it on. In the past, when I developed with Django, the server was usually hosted on localhost and with port 8080, so it's interesting to learn you can specify the port number. In addition, I don't have much experience with ssh, so it was interesting learning how to use it to access a remoote server. 
