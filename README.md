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

## Milestone4 Running Guide && Report

### Running Guide
In this project, I designed `JSONNode` class in `JSONObject.java` file  
to support stream operation.

Considering JSON are hierarchical structures, there can be many options  
to determine the type of stream we can support.  

In this milestone, I focus on `Leaf Elements Only`,   
so the stream operations will stream JSONObject's all leaf node to be its `JSONNode`.  

I wrote corresponding `toStream()` method in `JSONObject.java` file to support
stream operation and wrote corresponding unit test in `JSONObjectTest.java` 
called `testStreamWithJsonObject`

In the unit test, I created a JSONObject and do some stream process for  
leaf node(JSONNode), you can adjust the code to do more testing if you want.


## Milestone5 Running Guide & Report

### Running Guide
In this milestone, I introduced an enhancement to the library by adding an asynchronous version of the `toJSONObject` method. This new method allows for non-blocking XML to JSON conversion, enabling the client code to continue its execution and handle the results or errors through callback functions.

To use the asynchronous `toJSONObject` method, you can follow this example:

```java
XML.toJSONObject(reader, config, 
    (JSONObject jo) -> {
        // Success callback: handle the JSONObject (jo)
    },
    (Exception e) -> {
        // Error callback: handle the exception (e)
    }
);
```
Here, reader is the Reader object for the XML source, config is an instance of XMLParserConfiguration, and the two lambda expressions define the callbacks for handling success and error cases.


### Unit Tests
To ensure the correctness and efficiency of the asynchronous method, I wrote several unit tests:

`testToJSONObjectAsyncSuccess`: This test verifies that the method correctly parses a valid XML string into a JSONObject asynchronously.

`testToJSONObjectAsyncFailure`: This test checks that the method properly handles parsing errors and executes the error callback when parsing a malformed XML string.

`testMultipleToJSONObjectAsync`: This test demonstrates the method's ability to handle multiple XML to JSON conversions concurrently, processing two valid XML strings in parallel.

`testSuccessAndFailureToJSONObjectAsync`: This test runs two asynchronous operations in parallel, one expected to succeed and the other to fail, showcasing the method's ability to handle mixed scenarios concurrently.

### Performance Report
The addition of the asynchronous `toJSONObject` method significantly enhances the library's usability in scenarios involving large XML files or applications requiring non-blocking operations. By leveraging concurrent processing, the library can handle multiple XML to JSON conversions simultaneously, improving throughput and responsiveness in multi-threaded or I/O-bound environments.

This asynchronous approach not only optimizes performance but also provides flexibility in handling the results and errors, enabling more robust and scalable applications.

In conclusion, Milestone5 brings a crucial improvement to the XML to JSON conversion library, making it more versatile and suited for a wider range of applications, especially those requiring concurrent processing and non-blocking operations.