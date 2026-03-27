# Ex-7-INTERFACING-OF-KEYPAD-WITH-ARM-PROCESSOR

## AIM:
To write an embedded c program to interface keypad with ARM processor
## COMPONENTS REQUIRED:
### Hardware:
ARM 

PS2 Keyboard

### Software:
Coocox IDE
## PROCEDURE:
Step 1: Go to start All programs ◻ COIDE

Step 2: Give a suitable file name for your project and give the destination folder and then next Step 3: Go to chip◻ NXP◻ LPC 13XX◻ LPC1343◻ Next

Step 4: Select the required library file (SYSCON and GPIO) from the repository Step 5: A new project will be created

Step 6: Double click on main.c and type the program

Step 7: Add the required library source file to the project (Right click on include◻ Add file to group and
add the source file)

Step 8: Build the program using build option

Step 9: Flash the program by clicking on download code to flash Step 10: Interface the required component and note down the output ADD FILES:
### Repository:
CMSIS core, CMSIS boot, common header file, SYSCON, GPIO, IOCON, UART, SSP.

### Source files:
lcd.c, lcd.h,
## PROGRAM
```
#include <LPC17xx.h>
#include "lcd.h"
#include "delay.h"     
#include "gpio.h"
#define SWITCH1 P1_26
#define SWITCH2 P1_27
#define SWITCH3 P1_28
#define SWITCH4 P1_29

unsigned char key(void);

int main() 
{
 	
    SystemInit();
	
 	 
	LCD_SetUp(P1_18,P1_19,P1_20,P_NC,P_NC,P_NC,P_NC,P1_21,P1_22,P1_23,P1_24); 
    LCD_Init(2,16);
	
	LCD_Printf("**Key Pressed**");
   	GPIO_PinDirection(SWITCH1,INPUT);             /* Configure Switch pins as input */
    GPIO_PinDirection(SWITCH2,INPUT);
    GPIO_PinDirection(SWITCH3,INPUT);
	GPIO_PinDirection(SWITCH4,INPUT);  

  
    while (1) 
    {
       	char val=key();
	    LCD_GoToLine(1);
	    LCD_DisplayChar(val);
    }    
}
unsigned char key(void)
{
   char ch;
   	while(1)
	{
	  if(!GPIO_PinRead(SWITCH1))
	  {
	     DELAY_us(200);
		 ch='1';

		 break;
	  }
	  else if(!GPIO_PinRead(SWITCH2))
	  {
	  	DELAY_us(200);
	    ch='2';
	    break;
	  }
	  else if(!GPIO_PinRead(SWITCH3))
	  {
	  	DELAY_us(200);
	    ch='3';
	    break;
	  }
	  else if(!GPIO_PinRead(SWITCH4))
	  {
	  	DELAY_us(200);
	    ch='4';
	    break;
	  }	
	
	

	}
	return ch;
}
																		     
```
## OUTPUT
![WhatsApp Image 2026-03-17 at 11 00 59 AM](https://github.com/user-attachments/assets/11493e2d-8796-4fbd-b86e-59185822f42f)

## RESULT:
Thus an embedded c program to interface keyboard with ARM processor was executed and output was verified successfully
