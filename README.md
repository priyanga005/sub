; Assume BUFFER_1, BUFFER_2, and BUFFER_3 are predefined memory locations
; Each buffer holds 100 samples of signal data

MOV     R0, #0              ; Initialize index (R0 = 0)
MOV     R1, #BUFFER_1       ; Set R1 to the address of BUFFER_1
MOV     R2, #BUFFER_2       ; Set R2 to the address of BUFFER_2
MOV     R3, #BUFFER_3       ; Set R3 to the address of BUFFER_3

LOOP:
    LDR     R4, [R1, R0]    ; Load value from BUFFER_1 at index R0 into R4
    LDR     R5, [R2, R0]    ; Load value from BUFFER_2 at index R0 into R5
    SUB     R4, R4, R5      ; Subtract R5 from R4, result in R4
    STR     R4, [R3, R0]    ; Store the result into BUFFER_3 at index R0

    ADD     R0, R0, #1      ; Increment the index
    CMP     R0, #100        ; Compare index with 100 (end of buffer)
    BLT     LOOP            ; If index < 100, repeat the loop

; End of the program
