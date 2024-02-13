# MSWE262 Project Milestone2-5

## Milestone2 Running Guide && Report 

### Running Guide
In this project, I write 2 overload `toJsonObject` functions along with
2 different parse functions called: `parse2` and `parse3`  

You can use my unit test to simply verify its correctness
I wrote 4 unit tests:  

the first 2 unit tests is for function1: extract smaller json object and handle error  
called: `testJsonObjectWithJsonPointer` and `shouldHandleJsonObjectWithJsonPointerPathError`  

the second 2 unit tests is for function2: replace json object according to given path and handle error  
called: `testJsonObjectWithReplacement` and `shouldHandleJsonObjectWithReplacementPathError`


### Performance Report
We change the logic of the parse function in `parse2` and `parse3`  

In `parse2`, we add early return which means if we have already encountered  
the target tag we want to extract, we will stop parse and early return, so that we  
do not need to parse the whole xml file, it will improve the performance  


In `parse3`, we add early return which means if we have already encountered  
the target tag we want to replace, we will stop parse and early return, so that we  
do not need to parse the target tag smaller json object.   
In the scenario which the object we want to replace is very large, it will improve the performance.


## Milestone3 Running Guide && Report 

### Running Guide
In this project, I wrote 1 overload `toJsonObject` functions along with
1 parse functions called: `parse4`  

In the `toJsonObject` and `parse4`, the parameter of `YOURTYPEHERE`  
I chose `java.util.function Function` class to help me pass function as 
parameter into our function  

You can use my unit test to simply verify its correctness,  
I wrote 1 unit tests called `testJsonObjectWithKeyTransformer`  

In this test, you can define your own transformer function, in my test  
I define the behavior of adding prefix `swe262_` to the every key,    
you can define any other behavior to test if you want to :)  

### Performance Report
We change the logic of the parse function in `parse4`

In `parse4`, we apply key transformer function logic when we parse the XML file.    
So, comparing we parse the whole XML file and then do key transformer logic, it is
more efficient to do transform logic when parsing.  

In addition, we can change the key transformer logic by defining new function,   
so the method we overload also improve code re-usability.  
