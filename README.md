# x86 - 8086 Assembly programming

## Sub-Programs

| sub-program | function                  | register affected |
|-------------| -------------------------- | ----------------- |
| 2h          | display a character        | displays a character from register `dl`             |
| 1h          | accept keyboard input      | copies a character into register `al`               |
| 9h          | output a string            |                   |




## assembly program format

```assembly
	org 100h
	
	.model small             ;; the size of the program 
	.stack 100h              ;; the size of the stack 
	                         ;; the 100h denotes a hexadecimal number
	
	
	.code
	;; where your code resides

	ret
```


