# Lab Report 2: Servers and SSH Keys

The following shows an example and implementation of a web server called `StringServer`.

---
Here is the code for my `StringServer`:

```ruby
class Handler implements URLHandler {
        String print = "";
        int wordNum = 0;
    public String handleRequest(URI url) {
        
        if (url.getPath().equals("/")) {
            return String.format(print);
        } else if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                wordNum++;
                print = print + wordNum + ". " + parameters[1] + "\n";
                return String.format(print);
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


