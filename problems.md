# Max subset sum with no adjacent element

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

# Minimum number of coin change

```
function minCoins(coins, amount){
    const length = coins.length;
    let dp = new Array(amount+1).fill(Infinity);
    dp[0] = 0;
    for(let i=1; i<=amount; i++){
        for(let j=0; j<length; j++){
            if(coins[j]<=i){
                dp[i] = Math.min(dp[i], 1 + dp[i - coins[j]]);
            }
        }
    }
    
    return dp[amount] === Infinity ? -1 : dp[amount];
}

let coins = [1,2,5];
let amount = 11;

console.log(minCoins(coins, amount))

time complexity: The time complexity of the solution is O(amountn), where n is the length of the coins array.
space complexity: The space complexity of the solution is O(amount). 
```
