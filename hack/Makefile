
CC = gcc
#CFLAGS = -m32 -g
CFLAGS = -Wall -g

CURRENT_DIR=$(shell pwd)

TOOL_DIR=/home/pi/oss/RPI-HAT-Programmer/i2c0-eeprom/

.PHONY: all

all: hextool

hextool: hextool.c
	$(CC) $(CFLAGS) $< -o hextool

detect:
	i2cdetect -y 0

hack:
	cd $(TOOL_DIR) && ./eeprom_dump.sh
	cp $(TOOL_DIR)/eeprom_image.bin ./dslogic_eeprom.img
	cp dslogic_eeprom.img dslogic_eeprom_old.img
	./hextool -m -o 0x03   -n 1 -v 0x20 dslogic_eeprom.img
	./hextool -m -o 0x186a -n 1 -v 0x20 dslogic_eeprom.img
	mv dslogic_eeprom.img dslogic_eeprom_new.img

write:
	cd $(TOOL_DIR) && ./eeprom_write.sh $(CURRENT_DIR)/dslogic_eeprom_new.img

diff:
	xxd -g 1 dslogic_eeprom_old.img > dslogic_eeprom_old.txt
	xxd -g 1 dslogic_eeprom_new.img > dslogic_eeprom_new.txt
	echo "diff dslogic_eeprom_old.txt dslogic_eeprom_new.txt"

clean:	
	rm -f hextool dslogic_eeprom_*
