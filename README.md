# ft\_printf

ft\_printf is a simplified reimplementation of the standard C `printf` function, supporting the following conversion specifiers:

* **`%c`**: character
* **`%s`**: string
* **`%p`**: pointer (memory address)
* **`%d`, `%i`**: signed decimal integer
* **`%u`**: unsigned decimal integer
* **`%x`, `%X`**: unsigned hexadecimal integer (lowercase/uppercase)
* **`%%`**: literal percent sign

## File Structure

```
printf/
├── Makefile
├── ft_printf.c
├── ft_printf_utils.c
└── ft_printf.h
```

* **`ft_printf.c`**: implements `ft_printf`, parses format strings, and dispatches to helper functions.
* **`ft_printf_utils.c`**: utility functions for outputting integers, unsigned integers, hexadecimal, pointers, strings, and characters.
* **`ft_printf.h`**: function prototypes and header guards.
* **`Makefile`**: rules to build the static library `libftprintf.a`.

## Compilation

```bash
# Generate the static library
make

# Remove object files
make clean

# Remove objects and library
make fclean

# Rebuild from scratch
make re
```

After running `make`, you will have **`libftprintf.a`** in the project directory.

## Usage

1. Include the header in your source file:

   ```c
   #include "ft_printf.h"
   ```

2. Call `ft_printf` in place of `printf`:

   ```c
   int main(void) {
       ft_printf("Hello %s!\n", "world");
       ft_printf("Number: %d, Hex: %x\n", 42, 42);
       ft_printf("Pointer: %p\n", main);
       ft_printf("Percent sign: %%\n");
       return 0;
   }
   ```

3. Compile and link with the library:

   ```bash
   gcc -Wall -Wextra -Werror your_program.c -L. -lftprintf
   ```

## Examples

| Call                                       | Output             |
| ------------------------------------------ | ------------------ |
| `ft_printf("Char: %c\n", 'A');`            | `Char: A`          |
| `ft_printf("String: %s\n", "Hi");`         | `String: Hi`       |
| `ft_printf("Dec: %d, Hex: %X\n", 42, 42);` | `Dec: 42, Hex: 2A` |

## Limitations

* No support for field width, precision, or flags (e.g., `-`, `+`, ` `, `#`, `0`).
* Limited error handling; behavior on invalid formats may differ from standard `printf`.
* Only the specifiers listed above are implemented.

## Author

* **Alparslan Aslan** ([alaslan@student.42kocaeli.tr](mailto:alaslan@student.42kocaeli.tr))

## License

This project is provided without an explicit license. Use, modify, and distribute at your own risk.
