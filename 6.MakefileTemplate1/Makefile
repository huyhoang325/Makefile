DEBUG = 1
INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
CPPFLAGS = -I $(INCLUDE_DIR)
LDFLAGS =

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = mainDebug
else
CXXFLAGS += -O3
EXECUTABLE_NAME = mainRelease
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)

# Tự động tìm tất cả các tệp nguồn C++ trong thư mục nguồn
CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cc)
# Chuyển đổi danh sách các tệp nguồn .cc thành danh sách các tệp object .o trong thư mục build
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cc, $(BUILD_DIR)/%.o, $(CXX_SOURCES))

# Tạo thư mục build nếu chưa tồn tại
create:
	@mkdir -p $(BUILD_DIR)

# Biên dịch các tệp object và tạo tệp thực thi
build: create $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

# Thực thi chương trình thực thi đã được tạo ra
execute:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

# Xóa các tệp object và tệp thực thi trong thư mục build
clean:
	rm -f $(BUILD_DIR)/*.o
	rm -f $(BUILD_DIR)/$(EXECUTABLE_NAME)

# biên dịch các file .cc thành file .o
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cc
	$(CXX_COMPILER_CALL) -c $< -o $@
