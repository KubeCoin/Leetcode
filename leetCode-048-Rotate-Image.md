# 048. Rotate Image


## Method Best
如何旋转一个矩阵90度？
设想一个矩阵 n * n, 旋转90度相当于把他的
左上角 -> 右上角 -> 右下角 -> 左下角 -> 左上角
n 为偶数的时候，大矩阵可以分成四个小方阵。
n 为奇数的时候，矩阵可以分为中心的点和四个长比宽多1的长方形。
从左上的小矩阵开始循环，由于从0开始标记，
则一个边不超过 n/2.0, 或者说n/2向上取整；
一个边不超过 n/2, 或者说n/2向下取整；
举例，一个 3*3的矩阵，
1 2 3
4 5 6
7 8 9
我们取 1 2 或者 1 4 都行。
令 i,j 从0开始取值，
左上的坐标为 (    i    ,     j    )
右上的坐标为 (    j    , n - 1 - i)
左下的坐标为 (n - 1 - j,     i    )
右下的坐标为 (n - 1 - i, n - 1 - j）
例：
3 3 1 4 4
3 3 2 4 4
1 2 0 2 1
6 6 2 5 5
6 6 1 5 5


```Java
class Solution {
    public void rotate(int[][] matrix) {
        for( int i = 0; i < matrix.length/2.0; i ++ ){
            for ( int j = 0; j < matrix.length /2; j++){
                int c = matrix[i][j];
                matrix[i][j] = matrix[matrix.length-1-j][i];
                matrix[matrix.length-1-j][i] = matrix[matrix.length-1-i][matrix.length-1-j];
                matrix[matrix.length-1-i][matrix.length-1-j] = matrix[j][matrix.length-1-i];
                matrix[j][matrix.length-1-i] = c;
            }
        }
    }
}
```
