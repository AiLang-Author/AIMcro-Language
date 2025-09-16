# AIMacro Language

**For Python developers who want to retire with a full head of hair.**

## What is AIMacro?

AIMacro is a Python-compatible macro language that compiles to AILang assembly. It gives you Python's readability without the whitespace nightmares, clear block delimiters, and escape hatches to lower-level code when you need performance.

## Language Specification v3.2

### Core Syntax

```aimacro
# Functions with explicit end markers - no indentation errors!
def calculate(x, y):
    result = x + y;
    print(result);
    return result;
end;

# Or use 'func' for AIMacro native style
func main():
    values = range(10);
    total = 0;
    
    for val in values:
        total = total + val;
    end;
    
    return total;
end;
```

### Key Features

**No Whitespace Sensitivity**
- Blocks open with `:` and close with `end;`
- Semicolons terminate statements (optional but recommended)
- Mix tabs and spaces without breaking your code

**Python Compatibility**
- Use `def`/`pass` or `func`/`end`
- Built-in functions work as expected: `print()`, `len()`, `range()`, `str()`, `int()`
- Gradual migration path from Python

**Escape Hatches**
```aimacro
func optimize():
    # Drop to AILang for performance
    ailang {
        WhileLoop LessThan(i, 1000000) {
            ArraySet(buffer, i, 0)
            i = Add(i, 1)
        }
    };
    
    # Direct assembly when needed
    asm {
        MOV RAX, 60
        XOR RDI, RDI
        SYSCALL
    };
end;
```

### Parser Implementation

The AIMacro parser (v3.2) is written in pure AILang and includes:
- Python-style function call parsing
- Automatic built-in function translation
- AILANG and assembly escape blocks
- Clear error boundaries (no cascading indentation failures)

### Quick Start

```bash
# Compile AIMacro to AILang
./aimacro_parser your_code.aimacro > output.ailang

# Then compile AILang to executable
./ailang_compiler output.ailang
```

### Why AIMacro?

**Python's Problems:**
- Invisible whitespace bugs
- Tabs vs spaces holy wars  
- Copy-paste destroys indentation
- Silent scope errors

**AIMacro's Solutions:**
- Explicit `end;` markers
- Clear visual blocks
- Whitespace is just whitespace
- Compile-time scope validation

### Syntax Comparison

| Python | AIMacro | Benefit |
|--------|---------|---------|
| Invisible indentation | `:` and `end;` | Visual block boundaries |
| `def func():` | `def func():` or `func name():` | Compatible or cleaner |
| Whitespace sensitive | Semicolon terminated | No silent errors |
| No escape hatch | `ailang { }` blocks | Performance when needed |

### Coming Soon

- Full Python stdlib compatibility layer
- List comprehensions
- Generators via coroutines
- Class definitions
- Type hints (that actually do something)

### Philosophy

AIMacro isn't trying to replace Python - it's trying to save it from itself. Keep Python's elegant syntax and extensive ecosystem, but fix the foundational mistakes that cause developers endless frustration.

Write code that reads like Python, compiles like C, and never breaks because someone's editor converted tabs to spaces.

---

*AIMacro: Because life's too short to debug whitespace.*
