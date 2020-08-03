.data

String: .asciiz "Hello"
length: .word 5

.text

main:
	la $a0, String
	lw $a1, length
	
	jal funcReverse
	
	jal functPrintArrChar 
	
	li $v0, 10
	syscall
	
	funcReverse:
	
		move $t0, $a0
		move $t1, $a1
		addi $t2, $t1, -1 
		add $t9, $t0, $t2 
		div $t2, $t1, 2  
		add $t3, $zero, $zero 
		
		Loop:
			   
			 beq $t3, $t2, Exit
			
			 lb $t4, 0($t0)	
			 lb $t5, 0($t9)
			 
			 move $t6, $t4
			 sb $t5, 0($t0) 
			 sb $t6, 0($t9)
			 
			 addi $t0, $t0, 1
			 addi $t9, $t9, -1
			 addi $t3, $t3, 1 
			 
			 j Loop
				 		 
			 Exit: 

			 	jr $ra
	
	functPrintArrChar:
	 
		move $t0, $a0
			
		li $v0, 4
		move $a0, $t0
		syscall
			
		jr $ra
			 