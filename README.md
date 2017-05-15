# Blanks

## this is not intendet to be viable for anything usefull!
**(But I'm curious on what you manage to do with this)**

The base concept of this language is to annoy anyone that tries to work with it.
Thus any character used is a UNICODE whitespace, or otherwise unreadable.
Syntax is pretty straight forward: You type a command (e.g. ` `) followed by the argument (e.g. `    `) - Command or argument separators are not required as RAM has a fixed width of 16 bit (4 nibbles), 8 bit for NUMBERS and a single nibble for REG and arguments that may vary in length get prefixed with a matching indicator.

I would have like to tell you that you can write comments at the end of the line, but the line feed will terminate your application, so you'll have to write the whole code without comments or linebreaks. BUT, this language has one advantage over others (like brainfuck) where here you can use external code using the `　` command.

Now have fun (or not) with this masterpiece 👍

```
ram[65535]
reg[16] - implement as stack, programms may not pop at len 0, not pul at len 16
flag[b] - flags only change on add/sub
ip

U-000A ret     (exit the application and return reg [0] as exit code)
U-2000 pul RAM (set value to reg [0], shifts upwards)
U-2001 pop RAM (set ram to reg [0], shift downwards, fill with 0)
U-2002 add VAL (add VAL to reg [0], sets [b]ound flag on overflow)
U-2003 sub VAL (subtract VAL from reg [0], sets [b]ound flag on underflow)
U-2004 big IPI (jump ip if reg [0] is > 0 for +- {IPI}ncrement)
U-2005 sml IPI (jump ip if reg [0] is < 0 for +- {IPI}ncrement)
U-2006 flb IPI (jump ip if [b]ound flag is set)
U-2007 jmp IPI (just jump ip)
U-2008 tbl LEN (from ip+1 to ip+1+LEN search reg [0], load value from ip+1+LEN+found to reg [0] or ip+1+LEN+LEN otherwise)
U-2009 sys     (use OUT as input for a system() call, reg [0] will receive return value, INOUT binding will receive the first byte from the other apps STDOUT)

VAL/IPI may be a RAM, REG or LITERAL NUMBER
LEN is LITERAL NUMBER

output ram binding is 0xFF00-0xFFFF
input ram binding is 0xFE00-0xFEFF

U-0009	- indicate literal number
U-000A	- unused
U-000D	- indicate RAM
U-0020	- indicate REG
U-00A0	- Nibble 0
U-2000	- Nibble 1
U-2001	- Nibble 2
U-2002	- Nibble 3
U-2003	- Nibble 4
U-2004	- Nibble 5
U-2005	- Nibble 6
U-2006	- Nibble 7
U-2007	- Nibble 8
U-2008	- Nibble 9
U-2009	- Nibble A
U-200A	- Nibble B
U-200B	- Nibble C
U-202F	- Nibble D
U-205F	- Nibble E
U-3000	- Nibble F
```
