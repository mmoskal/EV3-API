## Copyright (c) 2015 Ahmad Fatoum
override PREFIX = arm-linux-gnueabi-
CC = $(PREFIX)gcc
AR = $(PREFIX)ar
SRCS = $(wildcard *.c)
OBJS = $(addprefix obj/,$(patsubst %.c,%.o,$(SRCS)))

.DEFAULT: libev3api.a
libev3api.a: $(OBJS)
	$(AR) rcs $@ $^
	
obj/%.o: %.c $(wildcard *.h)
	@mkdir -p obj
	$(CC) -mthumb -ffunction-sections -fdata-sections -Os -isystem. -c $< -o $@

#ifeq ($(OS),Windows_NT)
#RM = del /Q
#endif

.PHONY: clean npm
clean:
	$(RM) objs/*.o *.a *.d

npm: libev3api.a
	rm -rf npm
	mkdir npm npm/lib npm/include
	cp package.json ../README.md ../commands.pdf npm
	cp *.h npm/include
	cp *.a npm/lib
	cd npm; npm pack

