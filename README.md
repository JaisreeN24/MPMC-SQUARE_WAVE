
# SQUARE WAVE GENERATOR WITH FREQUENCY 50KHZ

## AIM
To write and execute an square wave with frequency 50khz in assembly and c program.

## APPARATUS REQUIRED
Personal Computer
Keil µVision Software

## PROGRAM
#### (i) USING ASSEMBLY LANGUAGE
ORG 0000H         
MOV TMOD, #01H    
AGAIN: MOV P1, #0FFH  
CALL DELAY
MOV P1, #00H    
CALL DELAY      
SJMP AGAIN      
DELAY: MOV TH0, #0FFH
MOV TL0, #0FAH
SETB TR0       
WAIT: JNB TF0, WAIT  
CLR TR0      
CLR TF0      
RET           
END

#### (ii)USING C LANGUAGE
#include <reg51.h>  
void delay(void);  
void main(void)
{
    TMOD = 0x01;  
    while(1)
    {
        P1 = 0xFF;  
        delay();   
        P1 = 0x00;  
        delay();
    }
}
void delay(void)
{
    TH0 = 0xFF;    
    TL0 = 0xF6;     
    TR0 = 1;       
    while (TF0 == 0);  
    TR0 = 0;        
    TF0 = 0;        
}

## OUTPUT:
<img width="752" height="619" alt="image" src="https://github.com/user-attachments/assets/5c9998c2-4319-4ea4-aaa2-8df43e1fe559" />
<img width="756" height="629" alt="image" src="https://github.com/user-attachments/assets/4953bba5-2548-40dc-bb36-e059442341ef" />


## RESULT:
Thus the square wave is generated using both assembly and C program an the output is shown.

