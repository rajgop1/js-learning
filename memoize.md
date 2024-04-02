# Memoization
*Memoization is a technique where we cache (store the data in some sort of hashmap) previous result of a function computation so that the function does not require to perform its computation again for the same arguments*

## How to?
*To Perform memoization usually a hashmap or object data structure is used*

## Example:
```
function fact(num){
  if(num===1)return 1
  return num * fact(num-1)
}
```
The above function will perform heavy computation recursively, if a number is large than the function call will also become larger, to avoid this we can cache previous results inside a hashmap
```
  function memoize(fn){
    const hashMap = {}
    return function(...args){
      if(args in hashmap){
        return hashmap[args]
      }
      const result = fn(...args)
      hashmap[args]=result
      return result
    }
  }
```
Now if we pass factorial function to above memoize function it will indeed return a new function which contains a hashmap in its lexical enviornment, or it have created a closure, now if we call the function
it will first check if the result is stored inside the hashmap, if its stored than it will return the stored result, else it will compute and store the result for furture so that provided same argunments
we do not need to call the function again and again...
