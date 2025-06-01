![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/test/badge.svg) ![](../../workflows/fpga/badge.svg)

# 🧠 Tiny Tapeout - ALU de 8 bits con Sumador Carry Look-Ahead

Este proyecto consiste en el diseño de una **Unidad Aritmético-Lógica (ALU)** de 8 bits que incorpora un **sumador tipo carry look-ahead**. La ALU permite realizar operaciones fundamentales como suma, resta, AND y OR. El diseño está preparado para ser fabricado mediante el flujo de desarrollo de [Tiny Tapeout](https://tinytapeout.com).

---

## ✅ Operaciones Soportadas

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

> Los operandos A y B se extienden internamente a 8 bits, completando con ceros a la izquierda.

---

## 📁 Organización del Proyecto

La estructura de archivos es la siguiente:

```
.
├── info.yaml
├── visual.json
├── user_module.v
├── user_project_wrapper.v
├── src/
│   ├── alu_8bit.v
│   ├── carry_lookahead_adder_8bit.v
│   └── user_module.v
├── test/
│   └── user_module_tb.v
├── docs/
│   └── README.md
```

---

## 🚀 Sobre Tiny Tapeout

[Tiny Tapeout](https://tinytapeout.com) es una iniciativa educativa que permite a estudiantes, aficionados y profesionales crear sus propios chips ASIC de manera sencilla y económica. Ideal para quienes quieren experimentar con diseño digital real.

---

## 🧪 Simulación del Diseño

Para simular el diseño localmente, sigue estos pasos:

1. Instala [OpenLane 2 usando nix](https://openlane2.readthedocs.io/en/latest/getting_started/nix_installation/index.html).
2. Clona el repositorio de herramientas de soporte:
   ```bash
   git clone -b tt06 https://github.com/TinyTapeout/tt-support-tools tt
   ```
3. Ejecuta el flujo de construcción:
   ```bash
   rm -rf runs && nix-shell ${OPENLANE2_ROOT}/shell.nix --run "python build.py"
   ```

También puedes correr una simulación directa con:

```bash
make sim
```

---

## 📚 Recursos Recomendados

- [Preguntas frecuentes de Tiny Tapeout](https://tinytapeout.com/faq/)
- [Lecciones de diseño digital](https://tinytapeout.com/digital_design/)
- [Siliwiz: explora cómo funcionan los semiconductores](https://tinytapeout.com/siliwiz/)
- [Únete al canal de Discord](https://discord.gg/rPK2nSjxy8)

---

## ✍ Autor

- **Francisco Mendez**

---

## 🛰 Próximos Pasos

- Sube tu diseño para la próxima ronda de fabricación en [tinytapeout.com](https://tinytapeout.com/#submit-your-design).
- Si mejoras el proyecto, no olvides actualizar este README.
- Comparte tu experiencia y tu chip en redes sociales usando el hashtag `#tinytapeout`:

  - [LinkedIn](https://www.linkedin.com/search/results/content/?keywords=%23tinytapeout)
  - [Mastodon](https://chaos.social/tags/tinytapeout)
  - [Twitter / X](https://twitter.com/hashtag/tinytapeout?src=hashtag_click)

