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

.PHONY: clean
clean:
	$(RM) objs/*.o *.a *.d
