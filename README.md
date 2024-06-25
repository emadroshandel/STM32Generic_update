A simple update on the STM32Generic Library is available at https://danieleff.github.io/STM32GENERIC/

Generic implementation of Arduino for STM32 boards using STM32 HAL.

I encountered difficulties using several peripherals when bit order determination was required. To troubleshoot the issue, I investigated the definitions of Least Significant Bit First (LSBFIRST) and Most Significant Bit First (MSBFIRST) in the original library. I found out these values have been defined in "Arduino.h" file available in "...\STM32GENERIC-master\STM32\cores\arduino" as follows:

#define LSBFIRST 0

#define MSBFIRST 1

I changed the above line with the following to provide type safety for these values.

enum BitOrder { LSBFIRST = 0, MSBFIRST = 1 };

This change solved the problem that I had for programming the SPI peripherals.

//Note: I may have changed the clock settings of some of the processors in this library. Please, check and update the settings based on your requirements in "Documents\Arduino\hardware\STM32GENERIC-master\STM32\variants\"target processor"\variant.c". I suggest using the STM32 cubeMX to update and adjust the clock setting. 




