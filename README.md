# HC-SR04 Driver for STM32

This is a driver for the HC-SR04 ultrasonic module written in C for the STM32 microcontroller.

## Usage

To use this driver, include the `main.c` file in your project and call the `read_distance()` function. This function will return the time in microseconds for which the echo pin was high, which can be used to calculate the distance to an object. The distance can be calculated using the following formula:

distance = (sensor_time * 0.034) / 2


## Example

```
#include "main.h"

int main(void)
{
  while (1)
  {
    uint32_t sensor_time = read_distance();
    double distance = (sensor_time * 0.034) / 2;
    printf("Distance: %f cm\n", distance);
  }
}
```

## Notes
- Make sure to include the necessary dependencies for the STM32 HAL and GPIO functions used in this driver.
- The trigger pin should be connected to PA1 and the echo pin should be connected to PA2. These can be changed in the MX_GPIO_Init() function.
- The driver uses the HAL delay function, which requires the system clock to be configured. Make sure to call SystemClock_Config() in your project.


![aa](https://user-images.githubusercontent.com/23439878/184652261-f91127e1-370a-427c-a383-e49a6ad08711.png)
