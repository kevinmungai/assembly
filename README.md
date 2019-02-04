# x86 - 8086 Assembly programming

## Sub-Programs

| sub-program | function                  | register affected |
|-------------| -------------------------- | ----------------- |
| 1h          | accept keyboard input      | copies a character into register `al`               |
| 2h          | display a character        | displays a character from register `dl`             |
| 9h          | output a string            |                   |




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


