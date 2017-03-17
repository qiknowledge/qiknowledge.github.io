## Knowledge base for Stata
* Userful commands
  - _`display`_ show the results of the command
  - Commands are case-sensitive
  - _`help`_ show the help file
  - _`sysuse`_ dir, dataname

    ![](assets\2017-03-12-19-28-30.png)
  - _`desc`_ describe the data

      ![](assets\2017-03-12-19-27-09.png)
  - _`summarize`_ followed by the variable name and it will run simple descriptive statistics
    
    ![](assets\2017-03-12-19-29-42.png)
   

  - _`list country gnppc if missing(gnppc)`_
    
    ![](assets\2017-03-12-19-31-10.png)
  - _`graph twoway scatter lexp gnppc`_ Draws a Scatterplot

    ![](assets\2017-03-12-19-34-25.png)
  - _`gen loggnppc = log(gnppc)`_ Compute new variables
  - _`regress lexp loggnppc`_ : Simple Linear Regression. <div style="background-color:red;"> Stata omits observations that are missing the outcome or one of the predictors </div>
    
     ![](assets\2017-03-12-19-40-29.png)
