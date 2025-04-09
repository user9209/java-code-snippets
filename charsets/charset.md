# Charset

The charset is responsible to represent a password or key.
Well known charsets are ASCCI, UTF-8 and also Base64, Hex, Decimal and others.

## Avoid optical confusion

|Charset|Remove chars|Bad chars|Description|
|----|--|---|--|
| [0-9] |  | 0 & 1 | only 10 elements, to not remove some |
| [A-Z] | I (i) & O (oh) & J (j) | I & O & J | i and j may collide as well as i, 1 and L|
| [a-z] | l (L) | l (L) | i, 1 and L may collide

|Symbol|Value|Alias|
|----|--|---|
|O|Zero|O 0|
|l|One|I l \\| 1|


See:

`I l J 1`  
`O 0`

## Avoid german and us & uk keyboard layout confusion

| Symbol DE | Symbol US |
| --------- | --------- |
| Z & z     | Y & y     |
| Y & y     | Z & z     |

## Special Characters - PW

English and german the same, using NUM!
````
! $ % . - +
````

Alternative:

Replace `$ %` caused variables in bash, batch, java and others.
Use `= #`:
````
! = # . - +
````

## Special Characters

|Char|PW|ASCII|UTF-8|Java|URL|C|Go|PHP|Python|DE=EN|
|----|--|-----|-----|----|---|-|--|---|------|-----|
|!|ok|ok|ok|||||||ok|
|$|ok|ok|ok|||||||ok|
|%|ok|ok|ok|||||||ok|
|&|ok|ok|ok||||||||
|=|ok|ok|ok||||||||
|?|ok|ok|ok||||||||
|+|ok|ok|ok|||||||NUM|
|*|ok|ok|ok|||||||NUM|
|~|ok|ok|ok||||||||
|#|ok|ok|ok||||||||
|.|ok|ok|ok|||||||OK|
|-|ok|ok|ok|||||||NUM|
|"||ok|ok||||||||
|§||fail|ok||||||||
|/||ok|ok|||||||NUM|
|(||ok|ok||||||||
|)||ok|ok||||||||
|[||ok|ok||||||||
|]||ok|ok||||||||
|{||ok|ok||||||||
|}||ok|ok||||||||
|\\ ||ok|ok||||||||
|'||ok|ok||||||||
|_||ok|ok||||||||
|:||ok|ok||||||||
|,||ok|ok||||||||
|;||ok|ok||||||||
|\\|||ok|ok||||||||


## QWERTZ

````
^ ° ! " § $ % & / ( ) = ?

{ [ ] } \

@ € + * ~
' #
< > | , ; . : - _
````

## QWERTY

````
~ ! @ # $ % ^ & * ( ) _ - + =
[ { ] } \ |
; : ' "
, < . > / ?
````

## Same
````
! $ % .
! $ % .
````
Using NUM
````
/ * - +
/ * - +
````

Not the same:
````
! " § $ % & / ( ) = ?
! @ # $ % ^ & * ( ) _
````

