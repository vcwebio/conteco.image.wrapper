[`image.wrapper`](../README.md) >> `executionplane` Library

-----

# `executionplane` Library

Standardised logging used by the API methods or other processing within the container image.

__`executionplane`__  [command] [arguments]    
Takes as arguments a method + arguments for execution.  
It pipes the output of `stdout` and `stderr` as an `executionplane-message` of type INFO or ERROR respectively.
It is used for functionality where there is no control over the output.  
It uses `executionplane-output-parser-stderr`, `executionplane-output-parser-stdout` and `executionplane-wait-for-output-parser`.

__`executionplane-capture-output`__ [command] [arguments]  
Execution of a method plus arguments with the output captured and stored into the environment variable CONTECO_EXECUTIONPLANE_OUTPUT.

__`executionplane-complete`__ [message]  
Shorthand for execution of `executionplane-message` with type _COMPLETED_.

__`executionplane-copied`__ [source >> destination]  
Executes `executionplane-message` with type _COPIED_ and includes source and destination if supplied.

__`executionplane-error`__  [error message]  
Executes `executionplane-message` with type _ERROR_ and includes error details if supplied.

__`executionplane-info`__  [information]  
Executes `executionplane-message` with type _INFO_ and includes information if supplied.

__`executionplane-invoke`__  [command] [arguments]  
Invokes a method with arguments.
It is used for methods that implement the executionplane API internally.
It does not allow recursive method calls.

__`executionplane-message`__  [type] [message details]  
Emits a message of [type] with [message details] if supplied.

__`executionplane-output`__  [command] [arguments]  
Auxiliary method that captures stdout into a file and to logging at the same time.

__`executionplane-output-parser-stderr`__  
Auxiliary method that wraps stderr in to JSON.  
Used by `executionplane-output` and `executionplane`.

__`executionplane-output-parser-stdout`__
Auxiliary method that wraps stderr in to JSON.  
Used by `executionplane-output` and `executionplane`.

__`executionplane-transparent`__  [command] [arguments]  
Logs the execution of a command using the _COMMAND_ message type.
Executes the command without interfering with the output.

__`executionplane-wait-for-output-parser`__  
Auxiliary method waits for the output parser process to conclude.  
Used by `executionplane-output` and `executionplane`.

__`executionplane-warning`__  [warning details]  
Executes `executionplane-message` with type _WARNING_ and includes warning details if supplied.

-----
[`image.wrapper`](../README.md) >> `executionplane` Library
