[`image.wrapper`](../README.md) >> `wrapper` Commandline Flags

-----

# `wrapper` Commandline Flags

## Default Behaviour

Invoked with no commandline arguments the container invokes the preset ENTRYPOINT and the output of `stdout` and `stderr` is wrapped within a ContEco JSON record.

If the first commandline argument doesn't match a `wrapper` flag, then it is interpreted as a bash command.

## Commandline Flags

Flags come in groups and have to be submitted in the right order.  
The flags are grouped in the order they should be submitted.

### First Group

The first group consists of two independent flags.

__`--executiontag`__  
Flag to submit a unique tag to the container. It must be first if submitted.  
The flag is used by the `executionplane` library to uniquely tag the log output.

__`--keepalive`__  (and __`--nokeepalive`__)  
(experimental) Flag to stop the container from exiting (or override to exit if already set). The container emits a keepalive record at 10 seconds interval.

## Second Group

The second group contains two mutually exclusive flags.

__`--interactive`__  
Forces the output of `stdout` and `stderr` to be emitted in  original (text) format, i.e. without the ContEco JSON wrapper.  
This can be set as default be setting environment variable CONTECO_INTERACTIVE=true using the __CONTECO_PREENTRYPOINT__ hook.

__`--container`__  
Forces the output of `stdout` and `stderr` to be emitted with a  ContEco JSON wrapper.

## Third Group

The third group contains three mutually exclusive flags.

__`--base`__  
Indicates that anything following this flag is to be passed on to the default entry point as arguments.

__`--extract`__  
Copies the internal git repository at `/conteco/repo` to the internal folder `/conteco/pwd` folder which is usually mapped to a host or named volume.

__`--help`__  
Prints the help file to `stdout`.

-----
[`image.wrapper`](../README.md) >> `wrapper` Commandline Flags
