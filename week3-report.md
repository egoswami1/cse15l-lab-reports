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

## Examples of Using the `/add-message` Command:

First Example:

<img width="511" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/1da0919e-3326-4273-a2f2-914a0d8d4f7c">

In this example, I typed a URL with a path containing the words, `/add-message`. This entire URL acted as the `URI uri` input for a new `handleRequest`. Within this program, the method first checks 