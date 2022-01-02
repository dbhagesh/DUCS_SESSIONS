# Bit Manipulation

What is Bit and Byte ?

## Operators
 - and
 - or
 - not
 - xor 
 - left shift
 - right shift

### Max Value of Integer

```
	32 bit numbers
	2^31 - 1 = 32 bits

```

### Odd and Even

```
 	number & 1 == 0 // Even
 	number & 1 == 1 // Odd
```
### Calculate power of 2

```
	1 << power
```

### Dividing a number by a power of 2

```
	number >> power
```

### Average of 2 numbers

```
	(x+y) >> 1
	low + ((high – low) >> 1)
```
### Multiply a number by a power of 2

```
	number << power
```

### Check if number is power of 2

```
	n & (n - 1) == 0
```

### Finding log2(n)

Logic:- We right shift x repeatedly until it becomes 0 mean while we keep count on the shift operations. This count value is the value of log to the base 2


```
	int log2(int x) {

	    int result = 0;
	    while( x >>= 1 ) {
	        result++;
	    }
	    return result;
	}
```

### Get, Set & Clear ith bit

```
	int getIthbit(int n, int i) {
	    return ( n & ( 1 << i) ) == 0 ? 0 : 1;
	}

	void setIthBit(int n, int i) {
	    n = n | (1 << i);
	}

	void clearIthBit(int n, int i) {
	    n = n & ( ~(1 << i));
	}
```

### Lower Case to Upper Case and Vice versa

```
	# Upper to lower
	ch |= ' ';
	ch = A (01000001) 
	mask = ' '  (00100000) 
	ch | mask = a (01100001) 

	# Lower to Upper
	ch &= '_';
	ch = a (01100001) 
	mask = '_' (11011111) 
	ch & mask = A (01000001) 

```

### How to flip all bits of a number if we are not allowed to use not operator

'''
	Hint Subtract the number from a number whose all bits are set
'''
### Count the number of ones in the binary representation of the given number

```
	int countBits(int n) {

    int count = 0;
    while (n > 0) {
        count += ( n&1 ); // n&1 is 1 only when LSB is 1
        n >>= 1; // performing right shift
    }
    return count;
}

// other way of counting set bits -> O(number of set bits)
int countBits(int n) {
    int count  = 0;

    while(n) {
        count++;
        n = n & (n-1); //Stripping off the lowest set bit :
    }
    return count;
}

// using builtin function
int countBits(int n) {
    return (int)__builtin_popcount(n);
}
```
### XOR APPLICATIONS
	
```	
 -  Application 1: In-Place Swapping
 -  Application 2: Finding the Missing Number
 -  Application 3: Finding the Duplicate Number
 -  Application 4: Finding Two Missing/Duplicate Numbers

 Refer here https://florian.github.io/xor-trick/

```
### Swapping of two numbers without using extra variable

```
	int x = 10, y = 5;
    // Code to swap 'x' (1010) and 'y' (0101)
    x = x ^ y; // x now becomes 15 (1111)
    y = x ^ y; // y becomes 10 (1010)
    x = x ^ y; // x becomes 5 (0101)

```

### Some Methods

```
// right propagate the rightmost 1-bit, 01010000=>01011111
int propagate(int x)
{
  return (x | (x-1));
}

// isolate the rightmost 0-bit, 10101011 => 00000100
int isolate0(int x)
{
  return (~x & (x+1));
}

// Turn on the rightmost 0-bit. 10100011 => 10100111
int turn0(int x)
{
  return (x | (x+1));
}
```

### Check Parity

```
	int checkParity(int n) {
	    return __builtin_parity(n);
	}
```

### Compute XOR from 1 to n

```
	int computeXOR(int n)
	{
	    if (n % 4 == 0)
	        return n;
	    if (n % 4 == 1)
	        return 1;
	    if (n % 4 == 2)
	        return n + 1;
	    else
	        return 0;
	}


	0  000 = 0 = n
 	1  001 = 1 = 1
	2  010 = 3 = n + 1
	3  011 = 0 = 0
	4  100 = 4 = n
	5  101 = 1 = 1
	6  110 = 7 = n + 1
	7  111 = 0 = 0
    8 1000 = 8 

    0  000 = 0 
 	1  001 = 1 
	2  010 = 3 
	3  011 = 0 
	4  100 = 4 
	5  101 = 1 
	6  110 = 7 
	7  111 = 0 
    
```

### More Methods

```
 Number of leading zeroes: builtin_clz(x)
 Number of trailing zeroes : builtin_ctz(x)
 Nu`mber of 1-bits: __builtin_popcount(x) 
```

### Problems

```
Q) Write a function to determine the number of bits you would need to flip to convert A to integer B ?
=> __builtin_popcount(A^B);

Q) Find XOR of numbers in a range (a,b)
=> f(a-1) ^ f(b)
   This XOR cancels out the XOR of f(a-1) 
   Now how to find XOR of these numbers ? Refer Above mentioned Method

Q) https://www.codechef.com/problems/XORORED
Q) https://www.codechef.com/problems/IRSTXOR

```
