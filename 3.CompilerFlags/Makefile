# Biến trong Makefile chỉ có thể là chuỗi
# Dấu nháy đơn hoặc nháy kép không có ý nghĩa đặc biệt đối với tên hoặc giá trị của biến trong Makefile


# Biến DEBUG xác định chế độ (gỡ lỗi hay tối ưu)
DEBUG = 1
# Tên của tệp thực thi sẽ được tạo
EXECUTABLE_NAME = main

# Tiêu chuẩn C++ 
CXX_STANDARD = c++17
# cảnh báo cho trình biên dịch C++
CXX_WARNINGS = -Wall -Wextra -Wpedantic
# Trình biên dịch C++ được sử dụng
CXX = g++
# truyền vào trình biên dịch C++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)

LDFLAGS =

# nếu chế độ DEBUG được bật, thêm các cờ gỡ lỗi và tắt tối ưu hóa
ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
else
# Nếu không, bật tối ưu hóa mức cao nhất
CXXFLAGS += -O3
endif

# Lệnh biên dịch hoàn chỉnh
COMPILER_CALL = $(CXX) $(CXXFLAGS)

# Biên dịch các file object 'my_lib.o' và 'main.o' thành chương trình thực thi
build: my_lib.o main.o
	$(COMPILER_CALL) main.o my_lib.o $(LDFLAGS) -o $(EXECUTABLE_NAME)

# Biên dịch 'main.cc' thành file object 'main.o'
main.o:
	$(COMPILER_CALL) main.cc -c

# Biên dịch 'my_lib.cc' thành file object 'my_lib.o'
my_lib.o:
	$(COMPILER_CALL) my_lib.cc -c

execute:
	./$(EXECUTABLE_NAME)

clean:
	rm -f *.o
	rm -f $(EXECUTABLE_NAME)
