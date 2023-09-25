
# stm
## Store Multiple
# stmdb
## Store Multiple, Decrement Before
`stmdb Rn{!}, reglist{^}`
### Example
`stmdb sp!,{r4, r5, r6}`
    This stores registers r4, r5 and r6 onto the stack.
    Before a register is stored onto the stack, the stack pointer is decremented by 0x04
    
    This is commonly done at the start of functions to free up those registers for that function to use,
        while still having a way to get back to those values once the function returns to it's parent function
    In this example I've used r4, r5 and r6 because registers r0, r1, r2 and r3 can be used to store a
        functions arguments. So assuming this function uses all those registers for it's arguments it doesn't
        make much sense to store them onto the stack when they're going to be used right away.
    Now you could do this, there's nothing stopping you from putting r0-r15 on the stack at the start of any
        function, but it's unnecessary. That is unless the function takes in more than 4 arguments. At this
        point it would be necessary to store the values of r4,r5,r[args] to the stack.


# ldm
## Load Multiple
# ldmia
## Load Multiple, Increment After
`ldmia Rn{!}, reglist{^}`
### Example
`ldmia sp!, {r4, r5, r6}`
    This loads values into registers r4, r5, r6 by reading the address the stack pointer is it and incrementing
        the stack pointer by 0x04 afterwards.
    

To put things in a much more succinct way from some random PDF I found on the internet:
```arm
stmdb sp!, {r4, r5, r6, r7} ; Push R4, R5, R6 and R7 onto the stack
... temporarily use R4,R5,R6,R7 for something else (like a function)
ldmia sp!, {r4, r5, r6, r7} ; Pop R4, R5, R6 and R7 from the stack
```


