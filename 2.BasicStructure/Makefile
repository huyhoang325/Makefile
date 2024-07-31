# Biên dịch các file object 'my_lib.o' và 'main.o' thành chương trình thực thi 'main'
build: my_lib.o main.o
	g++ main.o my_lib.o -o main

# Biên dịch 'main.cc' thành file object 'main.o'
main.o:
	g++ main.cc -c

# Biên dịch 'my_lib.cc' thành file object 'my_lib.o'
my_lib.o:
	g++ my_lib.cc -c

# Thực thi chương trình 'main'
execute:
	./main

# Xóa các file object (.o) và chương trình thực thi 'main'
clean:
	rm -f *.o
	rm -f main
