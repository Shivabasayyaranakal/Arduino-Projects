This project demonstrates how to blink an LED using a touch sensor with direct register-level programming on an Arduino UNO. The LED blinks only when the touch sensor is activated, showcasing efficient use of microcontroller resources and low-level programming techniques.
By bypassing high-level Arduino functions, the project emphasizes precise control over the hardware, making it an excellent learning exercise for understanding AVR microcontrollers.

CODE:
#define F_CPU 16000000UL // Define clock frequency 
#include <avr/io.h>      // Include AVR IO header 
#include <util/delay.h>  // Include delay function 
 
int main(void) { 
    // Step 1: Configure pin modes 
    DDRB |= (1 << PB0);  // Set PB0 (digital pin 8) as output for LED 
    DDRD &= ~(1 << PD2); // Set PD2 (digital pin 2) as input for Touch Sensor 
    PORTD |= (1 << PD2); // Enable pull-up resistor on PD2 
 
    while (1) { 
        // Step 2: Check if the touch sensor is triggered 
        if (!(PIND & (1 << PD2))) {  // Check if touch sensor output is LOW (active) 
            PORTB |= (1 << PB0);      // Turn on LED connected to PB0 
        } else { 
            PORTB &= ~(1 << PB0);     // Turn off LED connected to PB0 
        } 
    }
