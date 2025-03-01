## shiftr

### **Name**

**shiftr**(3) - \[BIT:SHIFT\] shift bits right

### **Syntax**

```fortran
result = shiftr(i, shift)
```

### **Description**

Returns a value corresponding to **i** with all of the bits shifted right by
**shift** places. If the absolute value of **shift** is greater than
**bit_size(i)**, the value is undefined. Bits shifted out from the
right end are lost, and bits shifted in from the left end are set to 0.

### **Arguments**

- **i**
  : The type shall be _integer_.

- **shift**
  : The type shall be _integer_.

### **Returns**

The return value is of type _integer_ and of the same kind as **i**.

### **Standard**

Fortran 2008 and later

### **See Also**

[**shifta**(3)](SHIFTA),
[**shiftl**(3)](SHIFTL)

###### fortran-lang intrinsic descriptions
