DEBUG = 1

CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS =

# Kiểm tra nếu chế độ DEBUG được bật, thêm các cờ gỡ lỗi và đặt tên tệp thực thi
ifeq ($(DEBUG), 1)
# Thêm cờ gỡ lỗi và tắt tối ưu hóa
CXXFLAGS += -g -O0
# Đặt tên cho tệp thực thi khi ở chế độ gỡ lỗi
EXECUTABLE_NAME = mainDebug
else
# Nếu không, bật tối ưu hóa mức cao nhất và đặt tên cho tệp thực thi
CXXFLAGS += -O3
EXECUTABLE_NAME = mainRelease
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS)

# Tự động tìm tất cả các tệp nguồn C++ trong thư mục hiện tại
CXX_SOURCES = $(wildcard *.cc)
# Chuyển đổi danh sách các tệp nguồn .cc thành danh sách các tệp object .o
CXX_OBJECTS = $(patsubst %.cc, %.o, $(CXX_SOURCES))


build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_NAME)

execute:
	./$(EXECUTABLE_NAME)

clean:
	rm -f *.o
	rm -f $(EXECUTABLE_NAME)

%.o: %.cc
	$(CXX_COMPILER_CALL) -c $< -o $@
