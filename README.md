ogre-demo-xcode6
================

Demo project working on Xcode 6 using Ogre 1.9 SDK compiled statically. I used the Xcode4 templates as a starting point and had to do some simple modifications to make it compile, basically compiling the SDK with the correct dependencies (particularly, <a href="http://www.boost.org/">Boost</a> is required for this demo to run) and adding some frameworks to the linking flags (CoreFoundation, Carbon, Cocoa).

I ran into some type mismatch errors with the OpenGL libraries that come in Mavericks (check out the following blog <a href="http://meandmark.com/blog/2011/11/sdl-opengl-typedef-redefinition-error-on-mac-os-x-10-7/">post</a>), I solved them by adding the following:

```cpp
#if defined(__APPLE__)  
	typedef void *GLhandleARB;
#else    
	typedef unsigned int GLhandleARB;
#endif
```

Basically, if you run into similar errors, change the type in the declaration so it matches the one the linker is asking for.
