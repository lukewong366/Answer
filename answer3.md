# Answer
function createArrayOfFunctions(y) {
  var arr = [];
  for(let i = 0; i<y; i++) {
   arr[i] = function(x) { return x + i; }
  }
  return arr;
}
 
// when we call createArrayOfFunctions(4)[1](4), there will return 4 (should be return 5)
// when we call createArrayOfFunctions(4)[2](4), there will return 4 (should be return 6)
// because "i" alway equal "y" when the "i" define by "var"
// For the below function, I will use "let" to replace "var" to define "i"
// beacause "var" is affect the global variable and "let" is only affect for loop variable(Block scope).

