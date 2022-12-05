
# 2022.12.5

## 矩阵归零

相关企业

给定一个 `*m* x *n*` 的矩阵，如果一个元素为 **0** ，则将其所在行和列的所有元素都设为 **0** 。请使用 **[原地](http://baike.baidu.com/item/原地算法)** 算法**。**

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/08/17/mat1.jpg)

```
输入：matrix = [[1,1,1],[1,0,1],[1,1,1]]
输出：[[1,0,1],[0,0,0],[1,0,1]]
```

**示例 2：**

![img](https://assets.leetcode.com/uploads/2020/08/17/mat2.jpg)

```
输入：matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]
输出：[[0,0,0,0],[0,4,5,0],[0,3,1,0]]
```

 

**提示：**

- `m == matrix.length`
- `n == matrix[0].length`
- `1 <= m, n <= 200`
- `-231 <= matrix[i][j] <= 231 - 1`

### 非原地算法,新引入了一个数组

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int[][]max = new int[matrix.length][matrix[0].length];
        for(int i = 0;i<matrix.length;i++){
            for(int j = 0;j<matrix[0].length;j++){
                max[i][j]=1;
            }}
        for(int i = 0;i<matrix.length;i++){
            for(int j = 0;j<matrix[0].length;j++){
                if(max[i][j]!=0) {
                    max[i][j] = matrix[i][j];
                }
                if(matrix[i][j]==0){
                    for(int k = 0;k<matrix[0].length;k++){
                        max[i][k] = 0;
                    }
                    for(int w = 0;w<matrix.length;w++){
                        max[w][j]=0;
                    }
                }
            }
        }
        for(int w = 0;w<matrix.length;w++){
            for(int j = 0;j<matrix[0].length;j++){
                matrix[w][j] = max[w][j];

            }
        }
    }
}
```
