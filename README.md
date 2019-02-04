# x86 - 8086 Assembly programming

## Sub-Programs

| sub-program | function                  | register affected | stored in `ah`                     |
|-------------| -------------------------- | ----------------- | ----------------------------------| 
| 1h          | accept keyboard input      | copies a character into register `al`               | yes |
| 2h          | display a character        | displays a character from register `dl`             | yes |
| 7h          | plays a 'bell sound'       | plays a 'bell sound' requires `2h` to run| no|   
| 9h          | output a string            |                   |                                    yes|
| 10d         | display line feed (or go the begining of the current line) |                     | no |
|13d          | carriage return (go to the next line) used in conjuction with `10d`  |           | no |

* the `d` stands for decimal while the `h` stands for hexadecimal.


## assembly program format

```assembly
;; this program does nothing

	org 100h
	
	.model small             ;; the size of the program 
	.stack 100h              ;; the size of the stack 
	                         ;; the 100h denotes a hexadecimal number
	
	
	.code
	;; where your code resides

start:                       ;; "start" this has no special meaning
                             ;; it is just a way to organize code
							 

	;; this is how assembly programs are ended

	mov ax, 4C00h            ;; "copy" 4C into 'ah' and 00 into 'al'
	int 21h                  ;; return control back to the operating system
	                         


end start                    ;; closes out the code organization

	ret
```


### Hello World

```assembly
	org 100h

	.model small
	.stack 100h
	
	
;; this is a 'pre-processor' that allows us to store data
;;  without thinking where in the world it is actually stored
;; all strings should end with a '$' sign to show termination

	.data        
hello_world db "Hello, World!", 13d, 10d, '$'	

	
	.code
	
start:
	mov ax, @data               ;; copy the pointer to 'data' into the 'ax' register 
	mov ds, ax                  ;; then move that pointer into the 'ds' register
	                            ;; 'ds' data segment register
								;; 'ds' can only use data that was stored in a previous register
	
	
	mov dx, offset hello_world  ;; set the beginning of the message into the 'dx' register
	                            ;; this makes it ready for displaying 
								;; by allowing access to the address of the 'data segment'

	mov ah, 9                   ;; '9' or '9d' or '9h' displays strings
	int 21h                     ;; return operation back to the operating system to allow execution
	
	
	
	;; ending the program
	mov ax, 4C00h
	int 21h
	


end start
	ret
```
