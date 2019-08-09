
INCLUDE_DIRECTORIES(/home/carl/usr/include/hello)
ADD_EXECUTABLE(main main.c)		
FIND_LIBRARY(myhello NEMES libhello.so PATHS "/home/carl/usr/lib")
TARGET_LINK_LIBRARIES(main ${myhello})
