# Lab Report Week 3
## Simplest Search Engine:
    import java.io.IOException;
    import java.net.URI;
    import java.util.ArrayList;

    class Handler implements URLHandler {

        ArrayList<String> stringsList = new ArrayList<>();

        public String handleRequest(URI url) {
            String output = "";
            if (url.getPath().equals("/")) {
                for(int i = 0; i < stringsList.size(); i++){
                    output = output + "\n" + stringsList.get(i);
                }
                return String.format("List of Strings: " + output);
            } else if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    stringsList.add(parameters[1]);
                    return String.format("String added: " + parameters[1]);
                }
                return "404 Not Found!";
            } else {
                if (url.getPath().contains("/search")) {
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].equals("s")) {
                        for(int i = 0; i < stringsList.size(); i++){
                            if(stringsList.get(i).indexOf(parameters[1]) != -1) {
                                output = output + "\n" + stringsList.get(i);
                            }
                        }
                        return String.format("Search: " + output);
                    }
                }
                return "404 Not Found!";
            }
        }
    }

    class SearchEngine {
        public static void main(String[] args) throws IOException {
            if(args.length == 0){
                System.out.println("Missing port number! Try any number between 1024 to 49151");
                return;
            }

            int port = Integer.parseInt(args[0]);

            Server.start(port, new Handler());
        }
    }
# Three Examples of Simple Search Engine
Initialization:

![image](https://user-images.githubusercontent.com/114527221/198497623-81cac93f-2caa-48ad-984f-870eb501b1a6.png)
![image](https://user-images.githubusercontent.com/114527221/198498093-d2737d89-352a-45fa-bddd-17426d6c1b53.png)

In the first screenshot, the server is initialized by calling the SearchEngine and setting a host number. Then I run the path "/add?s=pineapple" which adds a pineapple to the list of strings being held by the SearchEngine. This occurs because the method `handleRequest` is called. When the method is called, the url is taken and the method is run. Because the url contains the string "/add" the query (aka the part after the "?") is split up added to the array String variable, parameters. The second object in parameters is the word "pineapple" so we take the second index in parameters and add that word to the array list of words that the search engine is holding. And finally the website responds saying that the word was added to the list.

![image](https://user-images.githubusercontent.com/114527221/198499850-58d45f61-9dbd-4072-af6f-98f9a890c861.png)
![image](https://user-images.githubusercontent.com/114527221/198499908-11e3b0ed-ef0c-460a-afbc-6c8b8c260e21.png)
![image](https://user-images.githubusercontent.com/114527221/198500569-af6644d3-d83e-4b50-a46c-fcc6f1e198f6.png)

I add two more objects to the list and then I run a query for the term "apple". Like the "/add" code the "/search code" also inputs a url into the `handleRequest` method. Next the method runs. Because the url has the string "/search", the code attached to it is run. Like the "/add" url the "/search" code splits the query into two strings, with the second string being the key word that is being searched. A loop is ran to add the strings with the key string into an output string and then the output is presented onto the screen with all the words that have the key string. As you can see, the word "pear" is not presented even though it was added to the list because it does not contain the key word "apple".

![image](https://user-images.githubusercontent.com/114527221/198500821-658ff515-c1b5-4506-8140-63015b1608d5.png)

In this picture there is no query and the path is equal to "/". This runs the first if statement in the `handleRequest` method. A for loop is ran to add each string within the search engine list into an output string and then the string of words is printed onto the screen.



