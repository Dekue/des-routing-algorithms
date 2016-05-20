DAEMON_NAME = des-hello
VERSION_MAJOR = 2
VERSION_MINOR = 0
VERSION = $(VERSION_MAJOR).$(VERSION_MINOR)

CC = android-gcc
LIBS = -ldessert -lcli -shared
CFLAGS = -O0 -I$(DESSERT_LIB)/include -fpic
LDFLAGS = -L$(DESSERT_LIB)/lib -Wl,-rpath-link=$(DESSERT_LIB)/lib
SOURCE = src/$(addsuffix .c,$(DAEMON_NAME))

all: clean build package

clean:
	rm -f android.files/$(DAEMON_NAME) android.files/icon.png android.files/$(DAEMON_NAME)-$(VERSION).zip android.files/config.template android.files/daemon

.SILENT: clean

build:
	@echo 'Building target: $@'
	@echo 'Invoking: GCC C Linker'
	$(CC) $(CFLAGS) $(LDFLAGS) -o $(DAEMON_NAME) $(LIBS) $(SOURCE)
	@echo 'Finished building target: $@'
	@echo ' '

package: 
	mv $(DAEMON_NAME) android.files/daemon
	cp icon.png android.files/icon.png
	cp etc/defaultconfig android.files/config.template
	zip -j android.files/$(DAEMON_NAME)-$(VERSION).zip android.files/*
