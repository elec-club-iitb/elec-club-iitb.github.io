PROJECT = blink
OBJDIR = build

SRC = $(PROJECT).c
OBJ = $(OBJDIR)/$(PROJECT).o
ELF = $(OBJDIR)/$(PROJECT).elf
HEX = $(PROJECT).hex

all: $(SRC)
	mkdir -p $(OBJDIR)
	avr-gcc -g -mmcu=atmega32 -Os -DF_CPU=1000000 -c $(SRC) -o $(OBJ)
	avr-gcc -g -mmcu=atmega32 -Os -DF_CPU=1000000 -o $(ELF) $(OBJ)
	avr-objcopy -j .text -j .data -O ihex $(ELF) $(HEX)

burn:
	avrdude -p m32 -c usbasp -P usb -e -U flash:w:$(HEX)

clean:
	rm -rf $(OBJDIR)
