# Currying
Currying is a process in which we convert a function with multiple argument to multiple function with single argument

## Example:
	`
   function sum(a,b){
     return a+b
   }
  `
  to
  `
    function sum(a){
      return function(b){
        if(!b){return a}
        return sum(a+b)
      }
    }
  `

  // sum(2,3)
  // sum(2)(3)()
