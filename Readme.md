#  stack.8o
a chip8 stack implementation


##  to use

copy until the #tests# secion into your program, removing the
stack-buffer label and memory

call `push` to save registers `v0` - `vd` to the stack

call `pop` to restore registers `v0` - `vd` from the stack

if you attempt to pop from an empty stack or push to a full stack,
you will hit an [Octo](https://github.com/JohnEarnest/Octo) breakpoint - if your environment does not
support these (or you don't care to be warned) then remove lines
50 and 70.

you can allocate as much memory as you want to the stack by
copy/pasting line 25. **HOWEVER** make sure to increase the stack
size in increments of 14 and be sure to update `:stacklimit` to
reflect the new size.


## limitations

in order to save as many registers as possible, register `ve` is
used as a temporary register to load the stack pointer. This means
that pseudo comparisons (`<`, `<=`, `>`, `>=`) are unusable to check stack
boundaries. If you attempt to save a fewer number of registers to
the stack manually, you risk jumping over the hardcoded stack
boundaries.

using `push` and `pop` is fairly memory intensive, so this won't
perform well on hardware-emulating speeds.

TLDR

* only use push and pop to save registers to the stack
* be prepared to up your emulated cpu cycles
