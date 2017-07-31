# EasyDuilib
A simple and easy way to use duilib

Easyduilib库源自https://github.com/duilib/duilib
Easyduilib用CMAKE重新组织了源代码，使其更容易编译成静态库和动态库，更方便的集成到其他工程中。

静态库编译步骤：
1.运行generate.bat批处理，生成工程文件。
2.打开build目录下的duilib.sln就可以编译了。

动态库编译的方法与静态库一样，需要改CMakeLists.txt文件。
取消注释：
#add_definitions(-DUILIB_EXPORTS)
#add_library(duilib SHARED ${duilib_sources})

然后再注释上:
add_definitions(-DUILIB_STATIC)
add_library(duilib STATIC ${duilib_sources})