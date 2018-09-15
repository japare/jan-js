# Japare-search

Search utility for our japare project.
Pass search terms that describe a Japanese product you would like to import, receive JANs of products that fit those terms.



## Using the library's public interface

```javascript
const path = '/path/to/this/repository/index.js' //change path to match your file system, we're not on npm yet
const japare_search = require(path)

let keywords = ["Pikachu", "figure"] //enter your search keywords here

```

The lookup will return an array of Promises, which can be handled in two ways

#### A: Wait till all promises are fullfilled, then filter out the unsuccessful ones

```javascript

Promises.all(japare_search.lookup(jan))
.then(x => {
        if(x !== -1){
            console.log(x)
    });
```

#### B: Add then handler to each promise individually

WIP
<!-- ```javascript
let results = japare_search.lookup();
let filtered = results.forEach(x => { x.then({
                                        if(x !== -1){
                                            console.log(x);
                                    });
                                });
// or maybe rather this?
let mapped = results.map(x => { x.then({
                                        if(x !== -1){
                                            console.log(x);
                                    });
                                });
``` -->

## Structure of the result
Each promise will resolve as a jan on success

Each jan is either
  1. A 13 digit integer number, conforming to the ean / gtin13 standard 
  2. -1, which describes a failed lookup


## Testing if the library is working
1. Clone the repository to a directory of your choice
1. Open a terminal window in the directory
1. Let npm install dependencies
```bash
foo@bar:~$ npm install
```
4. Run the default test case
```bash
foo@bar:~$ npm test
```



## Planned features
In the future, we'd like to add the opportunity to choose or combine several lookup targets to get a more diverse result set.
Currently, myfigurecollection.com is the only available search targets.