# ALX Software Enginering Printf Team Project


This team project is a custom made printf fuction as part of the low-level programing
and algorithm track at ALX school. it as been optimized to take various input and
optional arguments based exactly on how the standard library function printf works. We submitted this as part the ALX software engineering course requirement for grading.


## Getting Started

These instructions will get you a copy of the project up and running on your local machine (Linux distro) for development and testing purposes.
Installing

You will need to clone the repository of the project from Github. This will contain the _printf function and all of its dependencies. No main.c file will be provided for testing, so you will need to create one.

git clone https://github.com/j-Apkan/printf.git

After cloning the repository you will have a folder called printf. In here there will be several files that allow the function to work.

### Synopsis

This function _printf() writes output to stdout, the standard output stream with the format and options without making use of any of the standard libary files it was written to use a local buffer of 1024 bytes hwne printing although it can print larger sets of data.

The _printf() functions return the total number of charcters printed to the stdout(excluding the null byte at the end of stringd) after a succesful excution.

if an output error is encountered, a negative avalue of -1 returned.

#### Header file

The header file is main.h.

  Prototype
1. int _printf(const char format ...);

format take a mandatory arguments and an extra number of argument can be none or many.

Format of string

format string is charcter string that start and end with double quotes. The format string is composed of zero or more directive; ordinary charcters(not %),, and conversion specifications.

Each conversion specification is introduced by the character % and ends with a conversion specifier. In between there may be (in this order):

    Zero or more flags

    An optional field width

    An optional precision modifier

    An optional length modifier

The flag characters

The character % may be followed by zero or more of the following flags:

    For o conversions, the first character of the output string is prefixed with 0 if it was not zero already.
    For x converions, 0x is prepended for non-zero numbers.
    For X conversions, 0X is prepeneded for non-zero numbers.

Example main.c:

    int main(void)
    {
    _printf("%#x\n", 7);
    }

Output:

     0x7

(space)

    A blank is left before a positive number or empty string produced by a signed conversion.

Example main.c:

     int main(void)
     {
    _printf("% d\n", 7);
     }

Output:

     7

+

    A sign (+ or -) is always placed before a number produced by signed conversion.
    Overrides a space flag.

Example main.c:

    int main(void)
    {
          _printf("%+d\n", 7);
    }

Output:

    +7

0

    For d, i, o, u, x, and X conversions, the converted value is padded on the left with zeroes rather than blanks.
    If the 0 flag is provided to a numeric conversion with a specified precision, it is ignored.

Example main.c:

int main(void)
{
    _printf("%05d\n", 7);
}

Output:

00007

-

    The converted value is left-justified (padded on the right with blanks instead of on the left with blanks or zeroes).
    Overrides a 0 flag.

Example main.c:

int main(void)
{
    _printf("%-5d7\n", 7);
}

Output:

7    7

Field Width

After flags, a minimum field width may be specified by a decimal digit string The first digit must be non-zero. If the converted value has fewer characters than the provided width, the output is padded on the left or right with spaces (depending on whether the - flag was provided).

Example main.c:

      int main(void)
     {
        _printf("%7d\n", 7);
     }

Ouptut:

      7

Alternatively, width may be provied as an argument using the * character For example, in the following: _printf("%*d\n", 6, 1); the argument 6 is considered the width for the conversion of the decimal 1

Precision

After any flags or provided width, a precision may be specified by a . followed by a decimal digit string. for d, i, 0, u, and x conversions, the precision specifies the minimum number of digit to appear for s and S conversions, the precision specifies the maximum charcter to rpinted.

After any flags or provided width, a precision may be specified by a . followed by a decimal digit string. For d, i, o, u, x, and X conversions, the precision specifies the minimum number of digits to appear. For s and S conversions, the precision specifies the maximum characters to be printed.

Example main.c:

int main(void)
{
    _printf("%.7d\n", 7);
}

Output:

0000007

Alternatively, precision may be provided as an argument using the * character after the .. For example, in the following: _printf("%.*d\n", 6, 1); the argument 6 is considered the precision for the conversion of the decimal 1.

Length Modifiers

After flags, width, and precision and before a conversion specifier, one of the following length modifiers may be provided:
h - Specifies that an integer conversion corresponds to a short int or unsigned short int argument.

Example main.c:

int main(void)
{
    _printf("%hd\n", SHRT_MAX);
}

Output:

32767

l - Specifies that an integer conversion corresponds to a long int or unsigned long int argument.

Example main.c:

int main(void)
{
    _printf("%ld\n", LONG_MAX);
}

Output:

9223372036854775807

The conversion specifier

The conversion specifier (introduced by the character %) is a character that specifies the type of conversion to be applied. The _printf function supports the following conversion specifiers:

d,i

The int argument is converted to signed decimal notation.

Example main.c:

int main(void)
{
    _printf("%d\n", 7);
}

Output:

7

b

The unsigned int argument is converted to signed decimal notation.

Example main.c:

int main(void)
{
    _printf("%b\n", 7);
}

Output:

111

o, u, x, X

The unsigned int argument is converted to unsigned octal (o), unsigned decimal (u), or unsigned hexadecimal (x and X). The letters abcdef are used for x conversions and the letters ABCDEF are used for X conversions.

Example main.c:

int main(void)
{
    _printf("%o\n", 77);
}

Output:

115

c

The int argument is converted to an unsigned char.

Example main.c:

int main(void)
{
    _printf("%c\n", 48);
}

Output:

0

s

The const char * argument is expected to be a pointer to a character array (aka. pointer to a string). Characters from the array are written starting from the first element of the array and ending at, but not including, the terminating null byte (\0).

Example main.c:

int main(void)
{
    _printf("%s\n", "Hello, World!");
}

Output:

Hello, World!

S

Identical to the s conversion specifier, except any non-printable characters in the array (ie. characters with an ASCII value < 32 or >= 127) are written as \x followed by the ASCII code value in hexadecimal (upper case, two characters).

Example main.c:

int main(void)
{
    _printf("%S\n", "Hello, World! Π");
}

Output:

Hello, World! \x0FFFFFFFFFFFFFFCE\x0FFFFFFFFFFFFFFA0

r Identical to the s conversion specifier, except characters from the array are written in reverse, starting from, but not including, the terminating null byte (\0) and ending at the first element of the array.

Example main.c:

int main(void)
{
    _printf("r\n", "Hello, World");
}

Output:

dlroW ,olleH

R

Identical to the s conversion specifier, except each character of the array is converted to its corresponding character in ROT13 before being written.

Example main.c:

int main(void)
{
    _printf("%R\n", "Hello, World");
}

Output:

Uryyb, Jbeyq

p

The address of the argument is written. The address is written in hexadecimal with a leading 0x.

Example main.c:

int main(void)
{
    char *str = "Hello, World";

    _printf("%p\n", (void *)str);
}

Output:

0x561a6d7bab5d

%

A % is written. No argument is converted. The complete conversion specification is %%.

Example:

int main(void)
{
    _printf("%%\n");
}

Output:

%

Submitted by

    Joseph Akpan  <J-Apkan>
    Abdulazeez Buhari  <AbdulTechX>
