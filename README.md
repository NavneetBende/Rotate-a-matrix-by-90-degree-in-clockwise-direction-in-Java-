Rotate a matrix by 90o in Java
Here, in this page we will discuss the program to rotate a matrix by 90o in Java Programming Language. We are given a row-wise sorted matrix of size r*c, we need to the rotate a matrix by 90o in clockwise direction.

Rotate a matrix by 90o in Java
Method 1 :
First transpose the matrix.
For this run a loop from i=0 to n and another loop from j=i+1 to j
After doing this, now iterate over rows and reverse each rows.
After this print the entire matrix (that gets rotated).
Time and Space Complexity :
Time-Complexity : O(n*n)
Space-Complexity : O(1)
Rotate a matrix by 90 degree in java
Method 1 : Code in Java
Run
import java.util.*;

class Main
{

  static void reverseRows (int mat[][])
  {
    int n = mat.length;
    for (int i = 0; i < mat.length; i++){
	    for (int j = 0; j <  mat.length/ 2; j++){
            int temp = mat[i][j];
            mat[i][j] = mat[i][n - j - 1];
            mat[i][n - j - 1] = temp;
	    }
    }
    
  }


  static void transpose (int arr[][])
  {
    for (int i = 0; i < arr.length; i++)
        for (int j = i; j < arr[0].length; j++){
	        int temp = arr[j][i];
	        arr[j][i] = arr[i][j];
	        arr[i][j] = temp;
	    }
  }

  static void printMatrix (int arr[][]){
        for (int i = 0; i < arr.length; i++){
	        for (int j = 0; j < arr[0].length; j++)
	            System.out.print (arr[i][j] + " ");
	        System.out.println ("");
        }
  }

  static void rotate90 (int arr[][])
  {
    transpose (arr);
    reverseRows (arr);
  }


  public static void main (String[]args)
  {
    int arr[][] = { {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12},
    {13, 14, 15, 16}
    };

    rotate90 (arr);
    printMatrix (arr);
  }
}
Output :
13 9 5 1
14 10 6 2
15 11 7 3
16 12 8 4
Method 2 :
First rotate the matrix about its main diagonal.
For this run a loop from i=0 to n and another loop from j=0 to 1, and swap (mat[i][j], mat[j][i])
Now, rotate the matrix about middle column.
For this run a loop from i=0 to n, and another loop from j=0 to n/2 and swap (mat[i][j],, mat[i][n-j-1]).
After this print the entire matrix (that gets rotated).
Time and Space Complexity :
Time-Complexity : O(n*n)
Space-Complexity : O(1)
Method 2 : Code in Java
Run
import java.util.*;
 
class Main{
 
    
    public static void main(String[] args)
    {
        int mat[][] = { { 1, 2, 3, 4 },
                        { 5, 6, 7, 8 },
                        { 9, 10, 11, 12 },
                        { 13, 14, 15, 16 } };
        int n=4;
 
        //Rotate the matrix about the main diagonal
        for(int i=0; i<n; i++){
            for(int j=0; j<i; j++){
               
                int temp = mat[i][j];
                mat[i][j] = mat[j][i];
                mat[j][i] = temp;
            }
                
        }

         //Rotate the matrix about middle column
        for(int i=0; i<n; i++){
            for(int j=0; j<n/2; j++){
                
                int temp = mat[i][j];
                mat[i][j] = mat[i][n-j-1];
                mat[i][n-j-1] = temp;
            }
        }
    
       
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                System.out.print(mat[i][j]+" ");
            }
            System.out.println("");
        }
        
    }
}


