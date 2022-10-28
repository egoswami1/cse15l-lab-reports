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
                return String.format("List of Strings: ", output);
            } else if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    stringsList.add(parameters[1]);
                    return String.format("String added: ", parameters[1]);
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
                        return String.format("Search: ", output);
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