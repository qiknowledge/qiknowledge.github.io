## Knowledge base for R language
* Book
  -The art of R Programming (Norman Matloff)
* Table of Content
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

* Book Notes
  - **Vector**
  ```R 
  x <- c(1,2,4) #create a vector
  x<- c(NULL,1,2) #Ignore NULL automatically
  x
  [1] 1 2
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
  ```R 
  x<-c(1,2,3)
  y<-c(4,5)
  z<-c(x,y) # Always use c
  z
  [1] 1 2 3 4 5
  ```
  - *obtaining the length of a vector*
  ```R 
  length (x) 
  [1] 5
  ```
  ```R
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
   ```R 
   c(1,2,3)+c(20,5)
   [1] 21 7 23 # giving a warning message by R 
   ```
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
    1:-5
    [1] 1 0 -1 -2 -3 -4 -5
    1.0:10.0 #convert numeric to integer automatically
    [1] 1 2 3 4 5 6 7 8 9 10
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
    ```R
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
    * Difference between NA and NULL
    NA: missing Data
    NULL: the value doesn't exist, rather than being existent but unknown
    Example:
    ```R
    x<-c(88,NA,12,168,13)
    x
    [1] 88 NA 12 168 13
    mean(x)
    [1] NA # NA cannot be skipped here
    mean(x,na.rm=T) # Setting NA remove to ture to skip NA 
    [1] 70.25
    x<- c(88, NULL, 12, 168, 13) # NULL means that the value doesn't exist
    mean(x)
    [1] 70.25
    ```
    There are multiple modes of NA
    ```R
    x<-c(5, NA, 12)
    mode(x[1])
    [1] "numeric"
    mode(x[2])
    [1] "numeric"
    y<-c("abc","def",NA)
    mode(y[2])
    [1] "character"
    mode(y[3])
    [1] "character"
    ```
    * Use of NULL
    1. To build up vectors in loops
      For example: build up a vector of the even numbers in 1:10
      ```R
      z<-NULL
      for (i in 1:10) if (i%%2==0) z<-c(z,i)
      z 
      [1] 2 4 6 8 10
      ```
      - NULL is a special R object with no mode
    * Filtering in R 
     1. Generating filtering indices
       ```R
       z<-c(5,2,-3,8)
       w<-z[z*z>8] # z*z>8 -> c(TURE, FALSE, TURE, TURE)
       w
       [1] 5 -3 8 #extract ture ones
       ```
       ```
       x<-c(1, 3, 8, 2, 20)
       x[x>3]<-0 # assignment
       x 
       [1] 1 3 0 2 0
       ```
    2. Filtering with the subset() function which can handle NA
       ```R
       x<- c(6,1:3,NA, 12)
       x 
       [1] 6 1 2 3 NA 12
       x[x>5]
       [1] 6 NA 12
       subset(x,x>5)
       [1] 6 12
       ```
    3. Using which() function to find the positions at which the condition occurs
       ```R
       z<-c(5,2,-3,8)
       which(z*z>8)
       [1] 1 3 4
       ```
       ```R
       first1a<-function(x)
       return(which(x==1)[1])
       ```
    * ifelse() function
      ```R
      ifelse(b,u,v) # b is a boolean vector, u and v are vectors
      ```
      ```R
      x<-1:10
      y<-ifelse(x%%2==0,5,12)
      y 
      [1] 12 5 12 5 12 5 12 5 12 5
      ```
      ```R
      x<-c(5,2,9,12)
      ifelse(x>6,2*x,3*x)
      [1] 15 6 18 24
      ```
      1. nest ifelse() function
      ```R
      g
      [1] "M" "F" "F" "I" "M" "M" "F"
      ifelse(g=="M",1,ifelse(g=="F",2,3))
      [1] 1 2 2 3 1 1 2
      ```
      ```
      ab[,1]<-ifelse(ab[,1]=="M",1,ifelse(ab[,1]=="F",2,3)) #gender information is stored in the first column of matrix ab
      ```
      ```
      # suppose we wish to form subgroups according to gender
      m<-which(g=="M")
      f<-which(g=="F")
      i<-which(g=="I")
      m 
      [1] 1 5 6
      f 
      [1] 2 3 7
      i 
      [1] 4
      ```
    * Testing vector equality
     ```
     # ==function is a vectorized function, so x==y applies the function ==() to the elements of x and y 
     # apply all() function
     x<- 1:3
     y<-c(1,3,4)
     x==y 
     [1] TRUE FALSE FALSE
     all(x==y)
     [1] FALSE
     ```
     ```
     identical(x,y)
     [1] FALSE
     # be careful
     x<-1:2
     y<-c(1,2) # produces floating-point numbers
     x 
     [1] 1 2
     y 
     [1] 1 2
     identical(x,y)
     [1] FALSE
     typeof(x)
     [1] "integer"
     typeof(y)
     [1] "double" 
     ``` 
   * Vector elements names
     ```R
     x<- c(1,2,4)
     names(x)
     NULL
     names(x)<-c("a","b","ab")
     names(x)
     [1] "a" "b" "ab"
     x 
     a b ab
     1 2 4
     ```
     ```R
     names(x)<-NULL # remove the names
     x 
     [1] 1 2 4
     ```
     ```R
     # reference elements of the vector by name
     x<-c(1,2,4)
     names(x)<-c("a","b","ab")
     x["b"]
     b 
     2
     ```
- **MATRICES AND ARRAYS**
  - Creating matrices 
   ```R
   y<- matrix(c(1,2,3,4),nrow=2,ncol=2) # in column-major order, you can set the byrow argument in matrix
   to indicate the data is coming in row-major order m<-matrix(c(1,2,3,4,5,6),nrow=2,byrow=T )
   y 
     [,1] [,2]
  [1,] 1   3    
  [2,] 2   4
  ```
  ```R
  y<-matrix(nrow=2,ncol=2)
  # then assign a value to each element
  ```
- Algebra operations
  ```R
  y%*%y # mathematical matrix multiplication
  3*y 
  y+y 
  ```
- Matrix indexing
  ```R
  # similar to vector: assign and negative subscripts
  ```
- Filtering on matrices
  ```R
  x 
    [,1] [,2]
    [1,] 1  2
    [2,] 2   3
    [3,] 3   4
    x[x[,2]>=3,] # if no "," the result will be shown as a vector  2 3 3 4
    [,1] [,2]
    [1,] 2   3
    [2,] 3   4
    x[x[,1]>1 & x[,2]>,  ]
    [1] 3 6 # Note that it gave us a two-element vector
  ```
- Applying functions to Matrix rows and columns
  - Apply function

    ```R
    apply(m,dimcode,f,fargs) # m is the matrix; dimcode is the dimention (rows:1,
    # columns:2);f is the function; fargs is an optional set of arguments to 
    # be supplied to f 
    z 
        [,1] [,2]
    [1,]  1   4
    [2,]  2   5
    [3,]  3   6
    apply(z,2,mean) # apply mean() to each column of z 
    [1] 2 5
    ```

    ```R
     z 
        [,1] [,2]
    [1,]  1   4
    [2,]  2   5
    [3,]  3   6
    f<-function(x) x/c(2,8)
    y<-apply(z,1,f)
    y                   # 2*3 rather than 3*2
    # if the function to be applied returns a vector of k components,
    # then the result will have k rows
         [,1] [,2] [,3]
    [1,]  0.5 1.000 1.50
    [2,]  0.5 0.625 0.75
    t(apply(z,1,f)) #using matrix transpose function t() if necessary
    ```
    ```R
    copymaj<-function(rw,d){
      maj<-sum(rw[1:d])/d 
      return(ifelse(maj>0.5,1,0))
    }
    x 
        [,1] [,2] [,3] [,4] [,5]
    [1,]  1   0    1    1    0
    [2,]  1   1    1    1    0
    [3,]  1   0    0    1    1
    [4,]  0   1    1    1    0
    apply(x,1,copymaj,3)
    [1] 1 1 0 1
    apply(x,1,copymaj,2)
    [1] 0 1 0 0
    ```
  - Adding and deleting matrix rows and columns
    ```R
    one
    [1] 1 1 1 1 
    z 
         [,1] [,2] [,3]
    [1,]  1     1   1
    [2,]  2     1   0
    [3,]  3     0   1
    [4,]  4     0   0
    z<-cbind(one,z) #rbind and cbind to add rows and columns to a matrix
    z 
          [,1] [,2] [,3] [,4]
    [1,]   1     1     1   1
    [2,]   1     2     1   0
    [3,]   1     3     0   1
    [4,]   1     4     0   0
    z<-z[c(1,3),c(1,2)]
    z 
          [,1] [,2] 
    [1,]   1     1   
    [2,]   1     3
    ```
  - Something different in matrix from vector
    ```R
    z 
         [,1] [,2] 
    [1,]  1     5  
    [2,]  2     6   
    [3,]  3     7  
    [4,]  4     8
    r<-z[2,] # to extract a row from a four-row matrix
    r 
    [1] 2 6 
    attributes(z)
    $dim
    [1] 4 2
    attributes(r) # r becomes vector format
    NULL
    str(z)
    int[1:4,1:2] 1 2 3 4 5 6 7 8
    str(r)
    int[1:2] 2 6
    r<-z[2,drop=FALSE] #suppress this dimension reduction
    r 
         [,1] [,2]
    [1,]  2    6
    dim(r)
    [1] 1 2
    # if you have a vector that you wish to be treated as a matrix
    u 
    [1] 1 2 3
    v<- as.matrix(u)
    attributes(u)
    NULL
    attributes(v)
    $dim 
    [1] 3 1
    ```
  - Naming matrix rows and columns 
    ```
    z 
         [,1] [,2] 
    [1,]  1     3  
    [2,]  2     4
    colnames(z)
    NULL
    colnames<-c("a","b") #rownames() works similarly
    z   
          a     b  
    [1,]  1     3  
    [2,]  2     4
    colnames(z)
    [1] "a" "b" 
    z[,"a"]
    [1] 1 2
    ```
  - Higher-Dimensional Arrays
    ```R
    firsttest
        [,1] [,2] 
    [1,]  46   30 
    [2,]  21   25   
    [3,]  50   50
    secondtest
         [,1] [,2] 
    [1,]  46   43 
    [2,]  41   35   
    [3,]  50   50
    # creating an Arrays
    tests<-array(data=c(firsttest,secondtest),dim=c(3,2,2)) 
    #first2: two portions of a test; second2: two layers
    attributes(tests)
    $dim
    [1] 3 2 2
    # R's print function for arrays display the data layer by layer
    tests
    , , 1
        [,1] [,2] 
    [1,]  46   30 
    [2,]  21   25   
    [3,]  50   50
    , , 2
         [,1] [,2] 
    [1,]  46   43 
    [2,]  41   35   
    [3,]  50   50
    ```
    
   - **Plot**
   - Histogram
    ![](histo.png)

  - **Matrix** <a id="Matrix"> </a>
  - **List**
  - **Dataframe**
  - **Function**

* Sources
  - [visualstudio](https://code.visualstudio.com/docs/?dv=win)

