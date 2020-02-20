[`image.wrapper`](../README.md) >> `wrapper` Library

-----

# `image.wrapper` Library

The library consists of 3 methods.  
`entrypoint` and `run-image` handle the commandline at container startup and `to-JSON` implements the ContEco JSON wrapper.

__`entrypoint`__  
Prepares the different __PATH__ environment variables for the `wrapper`. It sets the appropriate PATH for the `wrapper` execution.

It executes the __CONTECO_PREENTRYPOINT__ hook if one has been set.

Next if prepares the __PATH__ environment variables used by the `invoke` API entry point.

Finally it processes the first and second groups of commandline flags and hands processing to the `run-image` methods.


__`run-image`__  
This method emits the __wrapper__ JSON including the _keepalive_ record.  
It executes the process as set by the commanline.  

__`to-JSON`__  
Wraps the output from `stdout` and `stderr` line by line into a __ContEco__ JSON wrapper.  
It invokes `output-to-JSON` to filter / reshape the message output. Default behaviour is to leave the message unchanged. This method can be overridden by the image definition. `output-to-JSON` resides in `/conteco/bin`.  
The wrapper contains the following fields:
* __@timestamp__  
The timestamp of the wrapper creation.
* __origin__  
The originating container image: {CONTECO_TYPE}.{CONTECO_NAME}
* __source__  
The message source within the container, default is ___logger___.
* __level__  
The message level. Default is ___INFO___ for stdout and ___ERROR___ for stderr.
* __message__
The filtered / reshaped output line. Default is unchanged.

-----
[`image.wrapper`](../README.md) >> `wrapper` Library
