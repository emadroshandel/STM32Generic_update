A simple update on the SRM32Generic Library available at https://danieleff.github.io/STM32GENERIC/

Generic implementation of Arduino for STM32 boards using STM32 HAL.

The library, documented in https://danieleff.github.io/STM32GENERIC/, is a powerful tool for programming STM32 processors with various peripherals. I had difficulty in using several peripherals when bit order determination was required. I started to find out the problem what is the problem with the definition of Least Significant Bit First (LSBFIRST) and Most Significant Bit First (MSBFIRST) in the original library. I found out these values have been defined in "Arduino.h" file available in "...\STM32GENERIC-master\STM32\cores\arduino" as follows:

#define LSBFIRST 0

#define MSBFIRST 1

I changed the above line with the following to provide type safety for these values.

enum BitOrder { LSBFIRST = 0, MSBFIRST = 1 };

This change solved the problem that I had for programming the SPI peripherals.
