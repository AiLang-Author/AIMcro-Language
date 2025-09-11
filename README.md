# AIMcro Language
## A Python-Like Macro Language for AILang

### Executive Summary
AIMcro is a high-level macro language that compiles to AILang, offering Python-like simplicity without the whitespace footgun. It provides a clean, verb-first syntax with built-in OS services and zero imports required.

### Core Features

**Clean Syntax**
```aimcro
# No indentation errors - blocks use : and end;
func calculate x y:
  result = x + y;
  @print "Result: {result}";
  return result;
end;

# Macro calls use @ prefix
temp = @sensor.cpu.temp;
@display.text "CPU: {temp}°C";

# Natural word order
@file.write "data.txt" content;
```

**Key Advantages**
- **No imports needed** - All standard functionality built-in
- **Plain types** - Dynamic typing with automatic inference  
- **Inline AILang** - Escape hatch for performance-critical code
- **Macro libraries** - Pre-compiled system functions via @ syntax
- **Block clarity** - `:` opens, `end;` closes (no whitespace errors)

### Technical Design

**Transpilation Pipeline**
```
AIMcro Source → Parser → AST → AILang Code → x86 Assembly
```

**Macro System**
- System macros: `@sensor`, `@display`, `@file`, `@net`
- GUI macros: `@window`, `@button`, `@input`  
- Computation: `@math`, `@crypto`, `@hash`
- Direct OS service access through AILang runtime

### Example Application
```aimcro
# CPU monitor with GUI
window = @gui.create "System Monitor" 400 300;

loop:
  cpu = @sensor.cpu.temp;
  mem = @sensor.memory.used;
  
  @display.clear window;
  @display.text window "CPU: {cpu}°C" 10 10;
  @display.bar window mem 10 40 380 20;
  
  @time.sleep 1000;
end;
```

### Implementation Status
- **Phase 1**: Transpiler development (Q1 2026)
- **Phase 2**: Core macro libraries (Q2 2026)  
- **Phase 3**: Integration with AILang compiler (Q3 2026)

### Use Cases
- System utilities and monitoring tools
- Rapid GUI application development
- Educational programming environment
- Embedded systems control

### Design Philosophy
AIMcro eliminates programming ceremony while maintaining performance. Write code that reads like natural language, compiles to optimized assembly, and never worry about missing colons or incorrect indentation.

---
*AIMcro: Making AILang accessible to everyone*
