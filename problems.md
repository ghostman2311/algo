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

# Depth First Search

```
class Graph {
    constructor(){
        this.edges = {};
    }
    
    addVertex(v){
        this.edges[v] = {};
    }
    
    addEdges(u, v, weight){
        if(weight === undefined){
            weight = 0;
        }
        
        this.edges[u][v] = weight;
        this.edges[v][u] = weight;
    }
}

Graph.prototype.dfs = function(vertex, fn){
    const visited = {};
    
    this._dfs(vertex, fn, visited);
}

Graph.prototype._dfs = function(vertex, fn, visited){
    visited[vertex]=true;
    fn(vertex);
    
    for(let adjacentVertex in this.edges[vertex]){
        if(!visited[adjacentVertex]){
            this._dfs(adjacentVertex, fn, visited);
        }
    }
}

const g = new Graph();

g.addVertex(1)
g.addVertex(2)
g.addVertex(3)
g.addVertex(4)
g.addVertex(5)
g.addVertex(6)
g.addVertex(7)
g.addVertex(8)

g.addEdges(1,2)
g.addEdges(1,3)
g.addEdges(2,4)
g.addEdges(2,5)
g.addEdges(3,6)
g.addEdges(3,7)
g.addEdges(4,8)
g.addEdges(5,8)
g.addEdges(6,8)
g.addEdges(7,8)

console.log(g)

g.dfs(1, v => console.log(v);

DFS is a relatively efficient algorithm for traversing graphs, with a time complexity of O(V + E) and a space complexity of O(h), where V is the number of vertices, E is the number of edges, and h is the maximum depth of the graph.
```

# Matrix Spiral Order

```
matrix = [[1,2,3],[4,5,6],[7,8,9]]

function spiralTraverse(matrix) {
  const result = [];
  let rowStart = 0,
    rowEnd = matrix.length - 1,
    colStart = 0,
    colEnd = matrix[0].length - 1;

  while (rowStart <= rowEnd && colStart <= colEnd) {
    // Traverse right
    for (let i = colStart; i <= colEnd; i++) {
      result.push(matrix[rowStart][i]);
    }
    rowStart++;

    // Traverse down
    for (let i = rowStart; i <= rowEnd; i++) {
      result.push(matrix[i][colEnd]);
    }
    colEnd--;

    // Traverse left
    if (rowStart <= rowEnd) {
      for (let i = colEnd; i >= colStart; i--) {
        result.push(matrix[rowEnd][i]);
      }
      rowEnd--;
    }

    // Traverse up
    if (colStart <= colEnd) {
      for (let i = rowEnd; i >= rowStart; i--) {
        result.push(matrix[i][colStart]);
      }
      colStart++;
    }
  }
  console.log(result);
}
spiralTraverse(matrix)

The time complexity of the spiralOrder algorithm is O(m * n) where m is the number of rows in the matrix and n is the number of columns in the matrix.
The space complexity of the algorithm is also O(m * n) because the result array needs to store all the elements in the matrix, which can take up to O(m * n) space.
```

# Kadane's algorithms

```
function kadaneAlgorithm(arr){
    let maxSum = arr[0];
    let currentSum = arr[0];
    
    for(let i =1; i<arr.length; i++){
        currentSum = Math.max(arr[i], currentSum + arr[i]);
        maxSum = Math.max(currentSum, maxSum);
        
    }
    
    return maxSum
}

const arr = [-2,1, -3, 4,-1, 2,1,-5,4];

console.log(kadaneAlgorithm(arr));
Space complexity: O(1)
Time complexity: O(n);
```

