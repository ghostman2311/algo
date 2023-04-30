```
const A = [4, 1, 1, 4, 2, 1];


function maxSubsetSum(arr){
    const length = arr.length;
    if(length === 0){
        return 0;
    }
    
    if(length === 1){
        return arr[0];
    }
    
    const tempArr = new Array(length);
    tempArr[0] = arr[0];
    tempArr[1] = Math.max(arr[0], arr[1]);
    
    for(let i=2; i< length; i++){
        tempArr[i] = Math.max(tempArr[i-1], (tempArr[i-2] + arr[i]));
    }
    
    return tempArr[length-1];
}


console.log(maxSubsetSum(A))

Time  Complexity: O(n)
Space Complexity: O(n) //Space complexity can be improved to O(1)
Do it as excercise
```
