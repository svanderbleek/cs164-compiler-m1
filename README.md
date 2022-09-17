# cs164-compiler-m1

m1 port of berkeley cs164 "Programming Languages and Compilers"

## Runtime

Runtime can stay as is

```
#include <stdio.h>
#include <inttypes.h>

extern int64_t entry();

int main(int argc, char **argv) {
  printf("%" PRIi64, entry());
  return 0;
}
```

## Assembly

The assembly needs to be changed to

```
.global _entry
.align 2
_entry: 
	mov	X0, #42
	ret
```

## Commands

Object file from assembly

```
as -arch64 arm64 -o program.o program.s
```

Runtime

```
gcc -c runtime.c -o runtime.o
```

Executable

```
gcc program.o runtime.o -o program
```

## Links

* https://inst.eecs.berkeley.edu/~cs164/fa22/
* https://github.com/below/HelloSilicon
* https://tree-sitter.github.io/tree-sitter/
* https://github.com/bkomuves/toy-language-server
