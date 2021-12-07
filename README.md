# actions_between_matrices.cpp

#include <conio.h>
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;


//function which create a matrix1
int **creatingMatrix (int rows, int colums) {
    
  int **arr = new int *[rows];
  
  for (int i = 0; i < rows; i++){
      arr[i] = new int[colums];
    }
  return arr;
}


//function - filling in
void initialize (int **arr, int rows, int colums) {
  
  for (int i = 0; i < rows; i++){
      for (int j = 0; j < colums; j++){
	  arr[i][j] = rand () % 10 + 1;
	}
      cout << endl;
    }
}

//function - output
void funcOutput (int **arr, int rows, int colums){
    
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < colums; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }
}

//function - multiplication
void addit (int **arr1, int **arr2, int **arrResult, int rows, int colums) {
  for (int i = 0; i < rows; i++){
      
      for (int j = 0; j < rows; j++){
          for(int k = 0; k < rows; k++){
          arrResult[i][j] = arr1[i][j] * arr2[i][j];
          }
    }
}
}

//Freeing up memory
void freeingUp (int **arr, int rows){
    
  for (int i = 0; i < rows; i++ ){
		delete [] arr[i];
  }
	delete [] arr; 
}

int main (){
    srand (time (0));
    
    int rows, colums;
    int **arr1;
    int **arr2;
    int **arrResult;
  
  cout << "Please, enter number of rows: " << endl;
  cin >> rows;
  
  cout << " Please, enter number of columns: " << endl;
  cin >> colums;
  
  arr1 = creatingMatrix(rows, colums);
  arr2 = creatingMatrix(rows, colums);
  arrResult = creatingMatrix(rows, colums);
  
  cout << endl;

  cout << endl;
  
    initialize (arr1, rows, colums);
    initialize (arr2, rows, colums);
   
    addit(arr1, arr2, arrResult, rows, colums);
    
    funcOutput (arr1, rows, colums);
    cout << "-------------------------------------------" <<endl;
    
    funcOutput (arr2, rows, colums);
    cout <<"-------------------------------------------" <<endl;
    
    funcOutput (arrResult, rows, colums);
    cout << "-------------------------------------------" <<endl;
    
    
    freeingUp (arr1, rows);
    freeingUp (arr2, rows);
    freeingUp (arrResult, rows);
  

  return 0;
}



