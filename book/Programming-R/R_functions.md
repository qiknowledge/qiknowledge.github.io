## Useful functions in R
* Convert to Date

```R
as.Date(dateData, format = "")
```
![Date attributes](assets\2017-03-16-19-11-21.png)

* Filter data in dataframe

```R
my.data.frame = subset(data, V1 >2 | V2 < 4)
new.data = data[which(data$v1 > 2 | data$v2 <4), ] # which does prevent NA values from throuwing back unwanted results


```
