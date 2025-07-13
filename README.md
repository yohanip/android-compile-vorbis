# Compiling Vorbis for Android
Compiling Vorbis need Ogg

Compiling only Vorbis for Android will stuck on `find_package(ogg)`
because it will search on the `...llvm\sysroot` of the `ndk`

The path get appended even if specifying `-DOGG_ROOT`to some path 

So creating this parent adding `subdir` will manage to compile it successfully for Android

Steps

1. run python run.py
2. *tadaaaaaaaaaaaa!*