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




