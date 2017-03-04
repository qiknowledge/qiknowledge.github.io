## Knowledge base for R language
* Book
  -The art of R Programming (Norman Matloff)
* Table of Content
  - R
    - [Vector](#vector)
    - [Matrix](#Matrix)
    - [List]()
    - [Dataframe](#Dataframe)
  - [Method](#Method)
    - Clustering Method
      - K-means
        - Inroduction 
        - R package name / Matlab function
      - Fuzzy Clustering

      - Hierarchical Clustering

      - Clusters index

      - Comparsion with different clustering Method : Table
             
      - Principal Component Analysis
        - Mixed type of Pricipal Comonpoent Analysis
    
    - Classifiers 
      - CART / Decsion Tree
      - LDA
      - SVM
      - Neural Network



      
                



This is [an example][id] reference-style link.

[id]: http://example.com/  "Optional Title Here"  


* Book Notes
  - **Vector**<a id="vector"> </a>
  ```R
  x <- c(1,2,4) #create a vector
  ```
   - *Modes of the elements in a vector*
   integer, numeric, character(string),logical(Boolean),complex
  ```R
  typeof() #check the mode of a variable x
  ```
  - *Adding and deleting vector elements*
  ```R
  x <- c(88,5,12,13)
  x <- c(x[1:3],168,x[4]) #insert 168 before 13
  x
  [1] 88 5 12 168 13
  ```
  - *obtaining the length of a vector*
  ```R
  length (x)
  [1] 5
  ```
  ```
  first1 <- function(x){
      for (i in 1:length(x)){
          if (x[i]==1) break # break out of loop
      }
      return(i)
  } # application of length to determine the index of
  the first 1 value in x
  ```
   - Be careful coding that length(x) = 0
  ```R
  x <- c()
  x
  NULL
  length(x)
  [1] 0
  1: length(x)
  [1] 1 0
  1: -5
  [1] 1 0 -1 -2 -3 -4 -5
  ```
  - *A safety alternative of obtaining the length of a
  vector is to use the more advanced R function seq()*
  ```R
  x<-c(5,12,13)
  seq(x)
  [1] 1 2 3
  x<-NULL
  seq(x)
  integer(0)
  ```
  - *Declarations of vector*
  ```R
  y <- vector (length=2) # must create y first
  y[1]<-5
  y[2]<-12
  y<-c(5,12) # an alternative way
  ```
  - *Recycles*
    * R automatically recycles the shorter one, until it
   is long enough to match the longer one
  - *Common vector operations*
    * "+" "-" "/" "%%" done element by element
    * Negative subscripts mean that  we want to exclude
    the given elements in our output
    ```R
    z<-c(5,12,13)
    z[-1]  #exclude element 1
    [1] 12 13
    z[-1:-2] # exclude elements 1 through 2
    [1] 13
    ```
    ```R
    z<-c(5,12,13)
    z[1:(length(z)-1)] # more general to use length function
    [1] 5 12
    z[-length(z)]
    [1] 5 12
    ```
    * Generating useful vectors with the : operator
    ```R
    5:8
    [1] 5 6 7 8
    5:1
    [1] 5 4 3 2 1
    ```
    ```R
    i<-2
    1:i-1 #this means (1:i)-1, not 1: (i-1)
    [1] 0 1
    1:(i-1)
    [1] 1
    ```
    * Generating vector sequences with seq()
    ``` R
    seq(from=12,to=30,by=3)
    [1] 12 15 18 21 24 27 30
    ```
    * Repeating vector constants with rep()
      rep(x,times)
      ```R
      x<-rep(8,4)
      x
      [1] 8 8 8 8
      rep(c(5,12,13),3)
      [1] 5 12 13 5 12 13 5 12 13
      ```
      ```R
      rep(c(5,12,13),each=2)
      [1] 5 5 12 12 13 13
      ```
    * All() and any() functions to report whether any or
     all of their arguments are true
     ```R
     x<-1:10
     any(x>8)
     [1] TRUE
     any(x>88)
     [1] FALSE
     all(x>88)
     [1] FALSE
     all(x>0)
     [1] TRUE
     ```
    * Finding runs of consecutive ones
    ```R
    findruns <- function(x,k){
        n<-length(x)
        runs<-NULL
        for (i in 1:(n-k+1)){
            if (all(x[i:(i+k-1)]==1)) runs<-c(runs,i)
        }
        return(runs)
    }
    ```
    Alternative time saving way
    ```R
    fundruns1 <- function(x,k){
    n<-length(x)
    runs<- vector(length=n)
    count<-0
    for (i in 1:(n-k+1)){
        if (all(x[i:(i+k-1)]==1)){
            count<-count+1
            runs[count]<-i
        }

    }
    if (count>0){
        runs<-runs[1:count] # remove the unused portion of the vector
    } else runs <- NULL
    return(runs)
    }
    ```
    * predicting discrete-valued time series
    ```R
    preda<-function(x,k){
        n<-length(x)
        k2<-k/2
        #the vector pred will contain our predicted values
        pred<-vector(length=n-k)
        for (i in 1:(n-k)){
            if (sum(x[i:(i+(k-1))])>=k2) pred[i]<-1 else pred[i]<-0
        }
        return(mean(abs(pred-x[(k+1):n])))
    }
    ```
    ```
    predb<-function(x,k){
        n<-length(x)
        k2<-k/2
        pred<-vector(length(n-k))
        sm<-sum(x[1:k])
        if (sm>=k2) pred[1]<-1 else pred[1]<-0
        if(n-k>=2){
            for (i in 2:(n-k)){
                sm<-sm+x[i+k-1]-x[i-1]
                if (sm>=k2) pred[i]<-1 else pred[i]<-0
          }
        }
        return(mean(abs(pred-x[(k+1):n])))
    }
    ```
   - **Plot**
   - Histogram
    ![](histo.png)

  - **Matrix**<a id="Matrix"> </a>
  - **List**
  - **Dataframe**<a id="Dataframe"></a>
  - **Function**

* Sources
  - [visualstudio](https://code.visualstudio.com/docs/?dv=win)
