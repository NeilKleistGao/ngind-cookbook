
.. _namespace_ngind:

Namespace ngind
===============


This file includes the basic render component class declaration. Include this file if you need to create your own render component. 




.. contents:: Contents
   :local:
   :backlinks: none




Detailed Description
--------------------

This file includes the definition of quad data.

This file includes the implementations of quad.

This file defines the render program data.

This file includes the implementations of program.

This file includes the declaration of perspective class.

This file includes the implementations of perspective.

This file includes the factory for creating FFT font face data.

This file includes the implementation of font factory.

This file defines the platform tools in Linux.

This file define the world object that contains everything in game.

This file includes the implementation of world.

This file includes the interface of update-in-frames object.

This file define the most basic object class. Don't let your class inherit object unless you want to add some basic function. Add component to it instead.

This file includes the implementation of object.

This file includes the definition of entity object and lots of inline function for position/scale operation.

This file includes the implementation of entity object.

This file includes the declaration of memory pool.

This file includes the implementation of memory pool.

This file includes the definition of object for auto memory collectable object.

This file includes the implementation of auto collectable object.

This file includes the declaration of vectors in 2D space and their operations.

This file includes the implementations of vector class.

This file define the random number generator class by myself. Use this rather than srand/rand functions.

This file defines the logger factory. You should include this file rather than :ref:`file_ngind_kernel_log_logger.h`.

This file includes the implementations of logger factory.

This file declares the logger class. This file also includes the implementations of some template functions.

This file includes the implementations of logger class and initializes the static reference.

This file includes the declaration of log level.

This file includes text encoding type and text input manager. You should not visit text input class directly but use input class instead.

This file includes the implementation of :ref:`exhale_class_classngind_1_1TextInput`'s functions.

This file includes the mouse code and mouse input manager. You should not visit mouse input class directly but use input class instead.

This file includes the implementation of :ref:`exhale_class_classngind_1_1MouseInput`'s functions.

This file includes keyboard codes and keyboard input manager. You should not visit keyboard input class directly but use input class instead.

This file includes the implementation of :ref:`exhale_class_classngind_1_1KeyboardInput`'s functions.

This file includes the class used to deal with all input from users. Use this file directly rather than use some specific input class.

This file includes the implementation of :ref:`exhale_class_classngind_1_1Input`'s functions.

This file includes an output object based on stream only used in log system. Don't use it in general file output. Use :ref:`exhale_class_classngind_1_1File` class instead.

This file includes the implementation of :ref:`exhale_class_classngind_1_1OutputStream`'s functions.

This file includes the file object class's declaration. It may be easier and more convenient to access a file using file class. All file operations in this engine is based on it.

This file includes the implementation of :ref:`exhale_class_classngind_1_1File` class' functions.

This file includes the declaration and implement of coroutine class. There is only one class with 3 specialization classes.

This file includes the sprite render component class. This component's parent must be Entity :ref:`exhale_class_classngind_1_1Object` or the engine can't calculate the position, rotation and scale of texture. This file also includes the RTTR registration information. If you want to create object by using configuration files, you need provide a static method called create at least.

This file includes the implementation of Sprite :ref:`exhale_class_classngind_1_1Render`'s functions.

MIT License Copyright (c) 2020 NeilKleistGao Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all
 copies or substantial portions of the Software. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE. 





Classes
-------


- :ref:`exhale_struct_structngind_1_1QuadRenderCommand`

- :ref:`exhale_struct_structngind_1_1RenderCommand`

- :ref:`exhale_struct_structngind_1_1RGBA`

- :ref:`exhale_class_classngind_1_1AutoCollectionObject`

- :ref:`exhale_class_classngind_1_1Component`

- :ref:`exhale_class_classngind_1_1ConfigResource`

- :ref:`exhale_class_classngind_1_1Converter`

- :ref:`exhale_class_classngind_1_1Coroutine`

- :ref:`exhale_class_classngind_1_1Coroutine_3_01Type_00_01void_01_4`

- :ref:`exhale_class_classngind_1_1Coroutine_3_01void_00_01Param_8_8_8_01_4`

- :ref:`exhale_class_classngind_1_1Coroutine_3_01void_00_01void_01_4`

- :ref:`exhale_class_classngind_1_1EntityObject`

- :ref:`exhale_class_classngind_1_1File`

- :ref:`exhale_class_classngind_1_1FontFactory`

- :ref:`exhale_class_classngind_1_1FontResource`

- :ref:`exhale_class_classngind_1_1Game`

- :ref:`exhale_class_classngind_1_1Input`

- :ref:`exhale_class_classngind_1_1KeyboardInput`

- :ref:`exhale_class_classngind_1_1Logger`

- :ref:`exhale_class_classngind_1_1LoggerFactory`

- :ref:`exhale_class_classngind_1_1MemoryPool`

- :ref:`exhale_class_classngind_1_1MouseInput`

- :ref:`exhale_class_classngind_1_1Object`

- :ref:`exhale_class_classngind_1_1OutputStream`

- :ref:`exhale_class_classngind_1_1Perspective`

- :ref:`exhale_class_classngind_1_1PlatformUtils`

- :ref:`exhale_class_classngind_1_1PNGImage`

- :ref:`exhale_class_classngind_1_1Program`

- :ref:`exhale_class_classngind_1_1ProgramResource`

- :ref:`exhale_class_classngind_1_1Quad`

- :ref:`exhale_class_classngind_1_1Random`

- :ref:`exhale_class_classngind_1_1Render`

- :ref:`exhale_class_classngind_1_1RenderComponent`

- :ref:`exhale_class_classngind_1_1RenderQueue`

- :ref:`exhale_class_classngind_1_1Resource`

- :ref:`exhale_class_classngind_1_1ResourcesManager`

- :ref:`exhale_class_classngind_1_1Serializable`

- :ref:`exhale_class_classngind_1_1Shader`

- :ref:`exhale_class_classngind_1_1ShaderResource`

- :ref:`exhale_class_classngind_1_1SpriteRender`

- :ref:`exhale_class_classngind_1_1TextInput`

- :ref:`exhale_class_classngind_1_1Texture`

- :ref:`exhale_class_classngind_1_1TextureResource`

- :ref:`exhale_class_classngind_1_1Timer`

- :ref:`exhale_class_classngind_1_1TrueTypeFont`

- :ref:`exhale_class_classngind_1_1UpdatableObject`

- :ref:`exhale_class_classngind_1_1Vector2D`

- :ref:`exhale_class_classngind_1_1Window`

- :ref:`exhale_class_classngind_1_1World`


Enums
-----


- :ref:`exhale_enum_namespacengind_1a313a8f3ca7c14a64ad0b049e36be4038`

- :ref:`exhale_enum_namespacengind_1acfa48697abeb3c4cacbcc0876abe3edc`

- :ref:`exhale_enum_namespacengind_1a4a13b7a4609fb8501dde33d241d676f2`

- :ref:`exhale_enum_namespacengind_1a127513542f0c2c699bcb31387a5693b3`

- :ref:`exhale_enum_namespacengind_1a544c51930d91d9c27e016c77d8bfa90a`

- :ref:`exhale_enum_namespacengind_1aa1953eede8465f81541a6b6652ef6fdc`


Functions
---------


- :ref:`exhale_function_namespacengind_1a69245b0976a73a234ba8ff2b6daa0f4d`

- :ref:`exhale_function_namespacengind_1ae7da1debf28c9f0f49e2c0f500cee76b`


Variables
---------


- :ref:`exhale_variable_namespacengind_1ab380ee3776cf405284871307e34e3832`
