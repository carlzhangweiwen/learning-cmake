注意,静态库要使用 ARCHIVE 关键字
指令 ADD_LIBRARY
ADD_LIBRARY(libname
[SHARED|STATIC|MODULE]
[EXCLUDE_FROM_ALL]
source1 source2 ... sourceN)
类型有三种:
SHARED,动态库
STATIC,静态库
MODULE,在使用 dyld 的系统有效,如果不支持 dyld,则被当作 SHARED 对待。
EXCLUDE_FROM_ALL 参数的意思是这个库不会被默认构建,除非有其他的组件依赖或者手
工构建。


举个简单的例子:
INSTALL(TARGETS myrun mylib mystaticlib
RUNTIME DESTINATION bin
LIBRARY DESTINATION lib
ARCHIVE DESTINATION libstatic
)
上面的例子会将:
可执行二进制 myrun 安装到${CMAKE_INSTALL_PREFIX}/bin 目录
动态库 libmylib 安装到${CMAKE_INSTALL_PREFIX}/lib 目录
静态库 libmystaticlib 安装到${CMAKE_INSTALL_PREFIX}/libstatic 目录
特别注意的是你不需要关心 TARGETS 具体生成的路径,只需要写上 TARGETS 名称就可以
了
。


cd build
cmake -DCMAKE_INSTALL_PREFIX=/home/carl/usr ..

make 
make install
