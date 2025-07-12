# Compiling Vorbis for Android
Compiling Vorbis need Ogg

Compiling only Vorbis for Android will stuck on `find_package(ogg)`
because it will search on the `...llvm\sysroot` of the `ndk`

The path get appended even if specifying `-DOGG_ROOT`to some path 

So creating this parent adding `subdir` will manage to compile it successfully for Android

Steps

1. create directory, cd to the directory
2. clone vorbis https://gitlab.xiph.org/xiph/vorbis.git
3. clone ogg https://gitlab.xiph.org/xiph/ogg.git
4. clone this repository https://github.com/yohanip/android-compile-vorbis.git
5. cd to the android-compile-vorbis
6. run cmake commands
7. `cmake -B build -G Ninja -DANDROID_ABI=arm64-v8a -DANDROID_PLATFORM=android-21 -DANDROID_NDK=$ANDROID_NDK -DCMAKE_TOOLCHAIN_FILE=$ANDROID_NDK/build/cmake/android.toolchain.cmake -DCMAKE_INSTALL_PREFIX=build-published -DCMAKE_INSTALL_LIBDIR=lib -DCMAKE_INSTALL_INCLUDEDIR=include`
8. `cmake --build build/`
9. `cmake --install build/`
10. *tadaaaaaaaaaaaa!*