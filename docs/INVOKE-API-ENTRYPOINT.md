[`image.wrapper`](../README.md) >> `.invoke` API Entrypoint

-----

# `.invoke` API Entrypoint

Access to the API exposed by the image is through the `.invoke` entrypoint.

The method switches the PATH to the external API and then dispatches the invocation to the API method.

It also implements a `--help` flag for the API (`.invoke --help`) and its methods.

Access to the API is audited using the `executionplane` logging library.


-----
[`image.wrapper`](../README.md) >> `.invoke` API Entrypoint
