# ALU de 8 Bits con sumador CarrylookAhead - Tiny Tapeout

Este proyecto consiste en el diseño de una **Unidad Aritmético-Lógica (ALU)** de 8 bits que incorpora un **sumador tipo carry look-ahead**. La ALU permite realizar operaciones fundamentales como suma, resta, AND y OR. El diseño está preparado para ser fabricado mediante el flujo de desarrollo de [Tiny Tapeout](https://tinytapeout.com).

## 🧠 Funcionalidad

La ALU utiliza una señal de selección de 3 bits (`sel`) para determinar la operación a ejecutar:

| `sel` (3 bits) | Operación         |
|----------------|------------------|
| 000            | A + B (suma)     |
| 001            | A - B (resta)    |
| 010            | A & B (AND)      |
| 011            | A \| B (OR)      |
| Otros valores  | Resultado = 0    |

**Entradas:**
- `ui_in[7:0]`:  
  - `A[3:0]` = `ui_in[7:4]`  
  - `B[3:0]` = `ui_in[3:0]`  
  - `sel[2:0]` = `ui_in[2:0]`

**Salida:**
- `uo_out[7:0]`: resultado de la operación seleccionada
> Nota: A y B son extendidos a 8 bits internamente (relleno de ceros por la izquierda).

## 📁 Archivos principales

- `src/user_module.v`: Módulo compatible con Tiny Tapeout
- `src/alu_8bit.v`: ALU con operaciones aritmético-lógicas
- `src/carry_lookahead_adder_8bit.v`: Sumador optimizado tipo look-ahead
- `test/user_module_tb.v`: Testbench básico
- `info.yaml`: Metadatos del proyecto
- `user_project_wrapper.v`: Wrapper requerido por la plataforma
- `visual.json`: 

## ✍ Autor

- Francisco Mendez
