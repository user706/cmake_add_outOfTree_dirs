It is a MISTAKE to assume that the *main* CMakeLists.txt is always located in a toplevel directory, with all files BELOW that directory.
This mistaken assuption leads to a severe "BUG" in "cmake for visual studio".

Example: 
Here the *main* CMakeList.txt is located here: [target_device/full_variant/CMakeLists.txt](target_device/full_variant/CMakeLists.txt)  
And from there we call:
```cmake
add_subdirectory(../../common/utils    # code which is NOT in a subdirectory, but "out-of-tree"
                 utils_binary_dir      # build dir
                 ) 
```

This means that we go to out-of-tree builds  such as [common/utils/CMakeLists.txt](common/utils/CMakeLists.txt)  
which ARE NOT DISPLAYED PROPERLY in the new "cmake for visual studio".

This is a bug. It must be possible for me to see all the code.  
Thus: In the case where the *main* CMakeLists.txt pulls in stuff, which does not lie in a subdirectory BELOW the *main* CMakeLists.txt-directory, 
we must still be able to see that code.
