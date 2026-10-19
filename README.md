# ScuizyBytes VM

A lightweight, stack-based Virtual Machine (VM) written in Python, designed to demonstrate low-level execution concepts, instruction pointers, memory stack frames, and control flow jumps.

---

## Architecture Overview

ScuizyBytes executes instructions sequentially using an explicit **Instruction Pointer (IP)** within an execution loop (`while ip < len(program)`).

* **Architecture Type**: Stack-based
* **Execution Paradigm**: Linear evaluation with dynamic instruction jumps
* **Data Structure**: LIFO (Last-In, First-Out) stack

---

## Supported Instruction Set

| Instruction | Argument | Description |
| :--- | :--- | :--- |
| `PUSH` | `value` | Pushes an integer onto the top of the stack. |
| `SUB` | — | Pops two values ($b$, then $a$), subtracts $a - b$, and pushes the result. |
| `ADD` | — | Pops two values ($b$, then $a$), adds $a + b$, and pushes the result. |
| `JZ` | `target` | Pops the top stack value. If $0$, sets `IP` to `target`; otherwise increments `IP` by 1. |
| `JMP` | `target` | Unconditionally sets `IP` to `target`. |
| `PRINT` | — | Prints the current state of the stack. |
| `HALT` | — | Terminates VM execution. |

---

## Example Program Flow

```python
program = [
    "PUSH 3",  # IP 0: Push initial counter
    "PRINT",  # IP 1: Print current stack
    "PUSH 1",  # IP 2: Push decrement value
    "SUB",  # IP 3: Decrement stack value
    "JZ 6",  # IP 4: Jump to HALT if value is 0
    "JMP 1",  # IP 5: Loop back to PRINT
    "HALT",  # IP 6: Stop processor
]
```

---

## Getting Started

### Prerequisites
* Python 3.8+

### Execution
Run the interpreter script directly:

```bash
python ScuizyBytes.py
```

---

## Future Roadmap

- [ ] Add `PEEK` functionality to inspect stack elements without popping.
- [ ] Implement stack boundary checking and underflow safeguards.
- [ ] Add registers (`AX`, `BX`) alongside the stack.
- [ ] Implement conditional flags register (`ZERO_FLAG`).
- [ ] Port core architecture from Python to C/C++.
