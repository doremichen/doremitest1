OBJECTS = main.o
TARGET = hello

all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(CC) -o $@ $^

main.o: main.c version.h

version.h: new_header

new_header:
	@sed -e "s/<version>/$$(git describe)/g" \
		<version.h.in> version.h.tmp
	@if diff -q version.h.tmp version.h > dev/null 2>&1; \
	then \
		rm version.h.tmp; \
	else \
		echo "version.h.in ==> version.h" ; \
		cp version.h.in version.h; \
	fi

clean:
	rm -f $(TARGET) $(OBJECTS) version.h version.h.tmp
.PHONY: all clean
