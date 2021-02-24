Download and extract the binary from the file

This binary is a Stripped Binary

So,Lets use Ghidra to decompile the binary to generate source code

-----

Assume,

plvar1--->x

local_28--->msg

From this program,we can clearly see that, *x=1 is set initially

We need to make *x=0 to get the flag

-----

'x's address is being leaked from the printf() function

So we know the starting value of x's memory address

Whenever we pass a message the last index in the memory of msg(local_28) is being set to 0

msg[lastindex]=0

-----

To get the flag last index should be 0

*x=0

-----

So we should pass the message with the size of (leaked_address+1) as size to overwrite the memory

By passing the message as input,the pointer become *x=0 

And the flag will be shown from the file.(cat /flag)

-----

This is similar to OOB(Out OF Bound Vulnerability) which is common in dynamic malloc() pointers

Using these we can overwrite a specific memory address using dynamic pointers 