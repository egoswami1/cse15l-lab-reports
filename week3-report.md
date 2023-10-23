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

In this example, I typed a URL with a path containing the words, `/add-message`. This entire URL acted as the `URI url` input for a new `handleRequest`. Within this program, the method checks that the URL contains the string `add-message`. Because this is true, the method splits the query of the URL using the `getQuery()` method. The contents are stored in an array called `paramaters`. The contents of this array are ("s", "Hello"). The program then checks if the first element of the array is the string "s". Because it is, the integer variable, `wordNum` is incremented by 1. This variable keeps track of how words are stored within the `print` string. The `print` string stores all the words that are printed onto the server page. After `wordNum` is incremented, the second element of parameter, aka the content to be printed, is formatted into the `print` string and then returned by the method where it is brodcasted onto the webpage as "1. Hello". The print string reads, "1. Hello\n".

Second Example:

<img width="526" alt="image" src="https://github.com/egoswami1/cse15l-lab-reports/assets/114527221/fa146bbb-1197-4c08-8b14-2a4733b57234">

This example if similar to the first accept the starting value of `wordNum` is now 1 and the starting value of `print` is "1. Hello\n"In this example, I typed a URL with a path containing the words, `/add-message`. This entire URL acted as the `URI url` input for a new `handleRequest`. Within this program, the method checks that the URL contains the string `add-message`. Because this is true, the method splits the query of the URL using the `getQuery()` method. The contents are stored in an array called `paramaters`. The contents of this array are ("s", "Hello"). The program then checks if the first element of the array is the string "s". Because it is, the integer variable, `wordNum` is incremented by 1. This variable keeps track of how words are stored within the `print` string. The `print` string stores all the words that are printed onto the server page. After `wordNum` is incremented, the second element of parameter, aka the content to be printed, is formatted into the `print` string and then returned by the method where it is brodcasted onto the webpage as "1. Hello". The print string reads, "1. Hello \n".
