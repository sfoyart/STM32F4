TARGET=main.hex
EXECUTABLE=main.elf

CC=arm-none-eabi-gcc
#LD=arm-none-eabi-ld 
LD=arm-none-eabi-gcc
AR=arm-none-eabi-ar
AS=arm-none-eabi-as
CP=arm-none-eabi-objcopy
OD=arm-none-eabi-objdump

BIN=$(CP) -O ihex 

DEFS = -DUSE_STDPERIPH_DRIVER -DSTM32F4XX -DMANGUSTA_DISCOVERY -DUSE_USB_OTG_FS -DHSE_VALUE=8000000

MCU = cortex-m4
MCFLAGS = -mcpu=$(MCU) -mthumb -mlittle-endian -mfpu=fpv4-sp-d16 -mfloat-abi=hard -mthumb-interwork -std=c99
STM32_INCLUDES = -I/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Project/Peripheral_Examples/PWR_STOP \
	-I/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/CMSIS/ST/STM32F4xx/Include/ \
	-I/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/CMSIS/Include/ \
	-I/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/inc/ \
	-I/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_Device_Library/Class/hid/inc \
	-I/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_Device_Library/Core/inc/ \
	-I/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_OTG_Driver/inc/

OPTIMIZE       = -Os

CFLAGS	= $(MCFLAGS)  $(OPTIMIZE)  $(DEFS) -I./ -I./ $(STM32_INCLUDES)  -Wl,-T,stm32_flash.ld
AFLAGS	= $(MCFLAGS) 
#-mapcs-float use float regs. small increase in code size

STM32_USB_OTG_SRC = /home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_OTG_Driver/src/usb_dcd_int.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_OTG_Driver/src/usb_core.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_OTG_Driver/src/usb_dcd.c \

STM32_USB_DEVICE_SRC = /home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_Device_Library/Class/hid/src/usbd_hid_core.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_Device_Library/Core/src/usbd_req.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_Device_Library/Core/src/usbd_core.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32_USB_Device_Library/Core/src/usbd_ioreq.c

SRC = main.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Project/Peripheral_Examples/PWR_STOP/stm32f4xx_it.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Project/Peripheral_Examples/PWR_STOP/system_stm32f4xx.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Utilities/STM32F4-Discovery/stm32f4_discovery.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_syscfg.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/misc.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_gpio.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_rcc.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_exti.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_usart.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_i2c.c \
	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_spi.c 
#	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Project/Peripheral_Examples/PWR_STOP/stm32f4_discovery_lis302dl.c \
#	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Project/Peripheral_Examples/PWR_STOP/stm32f4_discovery_audio_codec.c \
#	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_adc.c \
#	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_dma.c \
#	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_flash.c \
#	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_tim.c \
#	/home/local/Downloads/STM32F4-Discovery_FW_V1.1.0/Libraries/STM32F4xx_StdPeriph_Driver/src/stm32f4xx_dac.c \



STARTUP = startup_stm32f4xx.S

OBJDIR = .
OBJ = $(SRC:%.c=$(OBJDIR)/%.o) 
OBJ += Startup.o

all: $(TARGET)

$(TARGET): $(EXECUTABLE)
	$(CP) -O ihex $^ $@

$(EXECUTABLE): $(SRC) $(STARTUP)
	$(CC) $(CFLAGS) $^ -lm -lc -lnosys -o $@

clean:
	rm -f Startup.lst  $(TARGET)  $(TARGET).lst $(OBJ) $(AUTOGEN)  $(TARGET).out  $(TARGET).hex  $(TARGET).map \
	 $(TARGET).dmp  $(TARGET).elf
