# Servers and Bugs
## Part 1
### Simplest Search Engine

```
import java.io.IOException;

import java.util.*;

import java.net.URI;

  

class Handler implements URLHandler {

  

    ArrayList<String> wordArray = new ArrayList<String>();

  

    public String handleRequest(URI url) {

        // for add method

        if (url.getPath().contains("/add")) {

            // split the string at "="

            String[] parameters = url.getQuery().split("=");

            // check if query correct (containing "s")

            if (parameters[0].equals("s")) {

                // add parameters[1] (the keyword we need) to wordArray

                wordArray.add(parameters[1]);

                // inform user that add is successful

                return String.format("Added '%s' to the list", parameters[1]);

            }

        } else if (url.getPath().equals("/search")) { // for seacrch method

            ArrayList<String> resultList = new ArrayList<String>();

            // split the string at "="

            String[] parameters = url.getQuery().split("=");

             // check if query correct (containing "s")

            if (parameters[0].equals("s")) {

                // for every word in wordArray, check if it contains

                // the query we're looking for

                // if yes, add to the resultList

                for (int i = 0; i < wordArray.size(); i++) {

                    String word = wordArray.get(i);

                    if (word.contains(parameters[1])){

                        resultList.add(word);

                    }

                }

                // print out the resultList

                return String.format("Words found: %s", resultList);

            } else { // print error if query is not correcy

                return "Error. Please check query syntax.";

            }

        } else {

            return "404 Not Found! Use a different path.";

        }

        return null;

    }

}

  

public class SearchEngine {

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

### How SearchEngine works

#### add
Here the `handleRequest` method is called, it checks if the request contains `add` . Then the request is split at `'='` to get the keyword we need to add.

![[Pasted image 20221027163405.png]]
The keyword here is `random`.


![[Pasted image 20221027165303.png]]
The keyword here is `apple`.

![[Pasted image 20221027165336.png]]
The keyword here is `pineapple`.


### search

Here the `handleRequest` method is called, it checks if the request contains `search` . Then the request is split at `='` to get the keyword we need to search. All the words containing the keyword is then added to an array list.

![[Pasted image 20221027165421.png]]


### incorrect syntax

The `handleRequest` method also checks if the request syntax is valid. Here the `search` request is missing `'s='` so it display an error message.

![[Pasted image 20221027165709.png]]

## Part 2

### reverseInPlace (from ArrayExamples.java)
#### Bug
Output gives an array that has the same first and last element.

![](https://lh5.googleusercontent.com/Yo1gp5UYaOYL47NbIRZGouyycXow_g9y10jBeyaogUqS-WyDm8pfHVGaf7Yz2xQG4eEu_j3KFlZg12t8I1JM1M-rkuG1HHz1-uVTR7jVd4HIK7dVT2QYzXizhZ1l0-WeBZoeSu2WaJ8dlDgU18RTug0mINsKLESf8m757f4EI42vz-cO8_o)

#### Symptoms
Wrong ouput

| Input     | Expected | Output    |
| --------- | -------- | --------- |
| {1, 2, 3} | {3,2,1}  | {3, 2, 3} |


#### Fix
Use a temp to swap elements, swap only half the length of the string.

![[Pasted image 20221027141824.png]]

### prepend (from LinkedListExample.java)

#### Bug
Infinite loop. n keeps pointing to the next node and appending.

![[Pasted image 20221027160908.png]]

#### Symptoms
Terminal "freezes" after running the tests, no ouput is given.

![[Pasted image 20221027161051.png]]


#### Fix
Move to the next node until we reach the last node (while loop). THEN append (outside of while loop).

![[Pasted image 20221027161201.png]]
