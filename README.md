# `image.wrapper` - Conteco

The 'image.wrapper' image holds the functionality common to all images in the __conteco__ and __modeco__ ecosystems.  
See `conteco.docs.overview` for more information on the ContEco ecosystem.

## Purpose

The _conteco.image.wrapper_ image is a store for all the common code-invariant functionality.  
Common functionality with a model dependent implementation is stored in the model images _conteco.model.*_.  
The wrapper image is used during the build process to inject the wrapper functionality into the newly build image.

## Common Functionality

This image is only concerned with common functionality that is code invariant and default implementations.  
These APIs are organised in subfolders of the `/conteco/bin` folder.  
The scripts in the `bin` folder itself can be overridden by any image.

## `bin` API

Location: `/conteco/bin`

The methods in the `bin` folder can be reimplemented by any of the images.
The subfolders of the `bin` folder are owned by specific images.

__`output-to-JSON`__  
This method provides the output from `stdout` to the JSON convertor when using the __ContEco__ JSON output format.  
By default no filter is applied. This can be overridden by all images.

## `controlplane` Lifecycle API

Location: `/conteco/extract/controlplane`

Each image contains an image specific implementations for the controlplane lifecycle methods.  
These methods are executed within the context of the `controlplane` image and are extracted just prior to execution.
This is the reason why they are stored in the `extract` folder.  
Image definitions can amend these methods as required using the `controlplane.base` external and internal API.

[`controlplane` API grouping in detail](./docs/IMAGE-CONTROLPLANE-API.md)  

## `image` API

Location: `/conteco/bin/image`

The `/conteco/bin/image` folder is the only folder added to the `$PATH` at container initialisation.  
It contains the API method invocation handler and a number of auxiliary methods:

__`invoke`__  
This method invokes methods of the image specific API.  
It adds the image specific API folder to the front of the `$PATH` for the duration of its execution.  
The method implements error handling for non-existent methods and a generic help file mechanism.  
Help files should be placed in `/conteco/help/<method>`.

__`image general purpose` API__  
The general purpose API contains useful auxiliary methods.

[`image general purpose` API in detail](./docs/IMAGE-GENERAL-PURPOSE-API.md)  

## `image.executionplane` API

Location: `/conteco/bin/image/executionplane`

This folder contains methods for internal use for the public API implementation.  
It consists of a number of logging methods to report on execution progress.

[`image executionplane` API in detail](./docs/IMAGE-EXECUTIONPLANE-API.md)

## `image.wrapper` API

Location: `/conteco/bin/image/wrapper`

The wrapper API manages container interaction with stdin, stdout and stderr.  
It is accessible using command line flags when instantiating the image.

[`image.wrapper` API Flags in detail](./docs/IMAGE-WRAPPER-API-FLAGS.md)

[`image.wrapper` API Methods in detail](./docs/IMAGE-WRAPPER-API.md)

## Folder Structure

The _image.wrapper_ image creates the base `conteco` folder structure for the wrapped image.  
The `conteco` folder container five subfolders:
- __`assets`__ containing image type and name subfolders holding files required for building and/or configuring the image.
- __`bin`__ containing executable files, in an image type and name subfolder structure.
- __`extract`__ containing files required by other images, contained in a subfolder structure with type and name of requesting image.
- __`pwd`__ the working folder of an image.
- __`repo`__ the image folder containing the git repository.
