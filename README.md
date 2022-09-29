# Leetcode

1.
// Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
// You may assume that each input would have exactly one solution, and you may not use the same element twice.

// You can return the answer in any order.

// Example 1:

// Input: nums = [2,7,11,15], target = 9 Output: [0,1] Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

const twoSum =  (nums, target)=> {

    let storage = {}
    
    for (let i = 0; i < nums.length; i++) {
    
      if (target - nums[i] in storage) {
      
        return [storage[target - nums[i]], i]
        
      } else {
      
        storage[nums[i]] = i;
        
      }
    }
  };
  
 --------------------------------------------------------------------------------------------------------------------------------------- 
  200. Number of Islands

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

 

Example 1:

Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
Example 2:

Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3

let numIslands = function(grid) {
    if ( grid == null || grid.length ==0)
            return 0;
        let noOfIslands = 0;
        for(let i = 0; i < grid.length;i++) {
            
        for (let j = 0; j < grid[i].length; j++) {
            
              if (grid[i][j] == '1') {
                noOfIslands+= dfs(grid,i,j);
                }
                
             }
        }
        return noOfIslands;
    }
    
    const dfs = function( grid, i, j) {
        
        if (i < 0 || i >=grid.length || j <0 || j >=grid[i].length || grid[i][j] =='0')
            return 0;
        grid[i][j] ='0';
        
        dfs(grid, i + 1, j);
        dfs(grid, i - 1, j);
        dfs(grid, i , j + 1);
        dfs(grid, i , j - 1);
        
        return 1;
    }

