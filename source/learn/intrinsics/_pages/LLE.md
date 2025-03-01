## lle

### **Name**

**lle**(3) - \[CHARACTER:COMPARE\] Lexical less than or equal

### **Syntax**

```fortran
result = lle(str_a, str_b)

   character(len=*),intent(in) :: str_a, str_b

      or

   character(len=*),intent(in) :: str_a, str_b(*) logical :: result
```

### **Description**

Determines whether one string is lexically less than or equal to another
string, where the two strings are interpreted as containing ASCII
character codes. if the **string_a** and **string_b** are not the same length,
the shorter is compared as if spaces were appended to it to form a value
that has the same length as the longer. Leading spaces are significant.

In general, the lexical comparison intrinsics LGE, LGT, LLE, and LLT
differ from the corresponding intrinsic operators .ge., .gt., .le., and
.lt., in that the latter use the processor's character ordering (which
is not ASCII on some targets), whereas the former always use the ASCII
ordering.

### **Arguments**

- **str_a**
  : variable or array of default _character_ type.

- **str_b**
  : variable or array of default _character_ type.

  if **str_a** and **str_b** are both arrays they must be of the
  same shape.

### **Returns**

- **result**
  Returns **.true.** if **STR_A \<= STR_B**, and **.false.** otherwise, based on
  the ASCII ordering.

### **Examples**

Sample program:

```fortran
program demo_lle
implicit none
integer             :: i
   write(*,'(*(a))')(char(i),i=32,126)
     write(*,*) lle('abc','ABC')              ! F lowercase is > uppercase
     write(*,*) lle('abc','abc  ')            ! T trailing spaces
     ! If both strings are of zero length the result is true.
     write(*,*) lle('','')                    ! T
     write(*,*) lle('','a')                   ! T the null string is padded
     write(*,*) lle('a','')                   ! F
     write(*,*) lle('abc',['abc','123'])      ! [T,F] scalar and array
     write(*,*) lle(['cba', '123'],'abc')     ! [F,T]
     write(*,*) lle(['abc','123'],['cba','123']) ! [T,T] both arrays
end program demo_lle
```

Results:

```text
  !"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ
  [\]^_`abcdefghijklmnopqrstuvwxyz{|}~
  F
  T
  T
  T
  F
  T F
  F T
  T T
```

### **Standard**

FORTRAN 77 and later

### **See Also**

[**lge**(3)](LGE),
[**lgt**(3),](LGT),
[**llt**(3)](LLT)

Functions that perform operations on character strings, return lengths
of arguments, and search for certain arguments:

- **Elemental:**
  [**adjustl**(3)](ADJUSTL),
  [**adjustr**(3)](ADJUSTR),
  [**index**(3)](INDEX),

[**scan**(3)](SCAN),
[**verify**(3)](VERIFY)

- **Nonelemental:**
  [**len_trim**(3)](LEN_TRIM),
  [**len**(3)](LEN),
  [**repeat**(3)](REPEAT),
  [**trim**(3)](TRIM)

###### fortran-lang intrinsic descriptions
