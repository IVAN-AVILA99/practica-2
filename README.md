PROCESSOR 16F887
    #include <xc.inc>
    ;configuración de los fuses
    CONFIG FOSC=INTRC_NOCLKOUT
    CONFIG WDTE=OFF
    CONFIG PWRTE=ON
    CONFIG MCLRE=OFF
    CONFIG CP=OFF
    CONFIG CPD=OFF
    CONFIG BOREN=OFF
    CONFIG IESO=OFF
    CONFIG FCMEN=OFF
    CONFIG LVP=OFF
    CONFIG DEBUG=ON
    CONFIG BOR4V=BOR40V
    CONFIG WRT=OFF
    
    PSECT udata
 mul:
    DS 1
    
PSECT resetVec,class=CODE,delta=2
    resetVect:
	PAGESEL main
	goto main
	
PSECT code
 num1:
    movwf 0b0110000
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
 num2:
    movwf 0b1101101
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
num3:
    movwf 0b1111001
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
num4:
    movwf 0b0110011
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
 num5:
    movwf 0b1011011
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
 num6:
    movwf 0b1011111
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
num7:
    movwf 0b1110000
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
num8:
    movwf 0b1111111
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
num9:
    movwf 0b1111011
    BANKSEL PORTB
    movwf PORTB
    PAGESEL main
    return
    
pausa:
    MOVLW   1			; 
    MOVWF   0x20
suma:
    incfsz  0x20,f		
    GOTO    suma
suma2:
    INCfsz  0x20,f		
    GOTO    suma2
     RETURN
    PSECT code
 main:
    BANKSEL PORTA
    BANKSEL TRISA
    clrf TRISA
    loop:
    PAGESEL num1
    call num1
    call pausa
    call num2
    call pausa
    call num3
    call pausa
    call num4
    call pausa
    call num5
    call pausa
    call num6
    call pausa
    call num7
    call pausa
    call num8
    call pausa
    call num9
    goto loop
    nop
    END
