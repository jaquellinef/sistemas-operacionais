# 🕰️ História dos Sistemas Operacionais

> 📚 **Tanenbaum — Sistemas Operacionais Modernos, 4ª edição**
> 📖 Capítulo 1 — História dos Sistemas Operacionais
> 🎯 Foco: evolução do hardware e dos sistemas operacionais

---

## 🌎 Visão geral

A história dos sistemas operacionais está diretamente ligada à evolução do **hardware**.

À medida que os computadores ficaram mais rápidos, menores e mais baratos, tornou-se necessário criar sistemas capazes de:

* ⚙️ controlar o hardware;
* 📦 organizar os trabalhos;
* 🧠 aproveitar melhor a CPU;
* 💾 gerenciar memória e armazenamento;
* 👨‍💻 facilitar a interação com o computador.

### 🧭 Linha do tempo

```text
1945          1955          1965          1980
 │             │             │             │
 ▼             ▼             ▼             ▼
🔥 1ª         ⚡ 2ª         🔬 3ª         🖥️ 4ª
geração       geração       geração       geração
 │             │             │             │
Válvulas     Transistores    ICs          PCs
 │             │             │             │
 │             ▼             ▼             ▼
 │           Batch       Multiprogramação
 │
 ▼
Programação
direta
```

---

# 🔥 1ª Geração — Válvulas

## 📅 1945–1955

Os primeiros computadores eletrônicos utilizavam **válvulas eletrônicas**.

Eram máquinas enormes, caras e difíceis de operar.

### Características

* 🔥 Produziam muito calor
* ⚡ Consumiam muita energia
* 🏢 Eram enormes
* 💰 Eram muito caras
* ❌ Apresentavam baixa confiabilidade
* 👨‍💻 A programação era extremamente trabalhosa

```text
       🖥️ COMPUTADOR

┌─────────────────────┐
│ 🔥 🔥 🔥 🔥 🔥 🔥 │
│ 🔥    VÁLVULAS    🔥│
│ 🔥 🔥 🔥 🔥 🔥 🔥 │
└─────────────────────┘
```

### 👨‍💻 Como os programas eram executados?

Não existiam sistemas operacionais modernos.

O programador precisava trabalhar **diretamente com a máquina**.

```text
👨‍💻 Programador
       │
       ▼
🖥️ Hardware
       │
       ▼
📊 Resultado
```

A preparação dos programas podia ser extremamente demorada.

---

# ⚡ 2ª Geração — Transistores

## 📅 1955–1965

Os **transistores** substituíram as válvulas.

Essa mudança foi fundamental para a evolução dos computadores.

```text
🔥 Válvulas
     │
     │ evolução
     ▼
⚡ Transistores
```

### 🚀 Principais melhorias

| Válvulas 🔥      | Transistores ⚡  |
| ---------------- | --------------- |
| Grandes          | Menores         |
| Muito calor      | Menos calor     |
| Alto consumo     | Menor consumo   |
| Pouco confiáveis | Mais confiáveis |
| Caras            | Mais acessíveis |
| Mais lentas      | Mais rápidas    |

---

# 📦 Sistemas em Lote — Batch

Com computadores mais rápidos, surgiu um novo problema:

> ❓ Como evitar que a máquina ficasse parada enquanto alguém preparava o próximo programa?

A solução foi agrupar vários trabalhos em **lotes**.

```text
┌─────────┐
│ 📄 Job 1│
├─────────┤
│ 📄 Job 2│
├─────────┤
│ 📄 Job 3│
├─────────┤
│ 📄 Job 4│
└────┬────┘
     │
     ▼
┌──────────────┐
│ 🖥️ COMPUTADOR│
└──────┬───────┘
       │
       ▼
📊 Resultados
```

Em vez de executar:

```text
Job 1
↓
intervenção humana
↓
Job 2
↓
intervenção humana
↓
Job 3
```

os trabalhos eram preparados para execução em sequência:

```text
Job 1 → Job 2 → Job 3 → Job 4
```

### 🎯 Objetivo

**Aumentar a utilização do computador e reduzir o tempo desperdiçado entre trabalhos.**

---

# 🔬 3ª Geração — Circuitos Integrados

## 📅 1965–1980

A próxima grande evolução veio com os **circuitos integrados (ICs)**.

```text
🔥 Válvulas
     ↓
⚡ Transistores
     ↓
🔬 Circuitos Integrados
```

Os computadores ficaram:

* 🚀 mais rápidos;
* 📦 menores;
* 💰 mais baratos;
* ✅ mais confiáveis;
* 🧠 mais poderosos.

Mas a principal mudança para os sistemas operacionais foi o surgimento da:

# 🧠 Multiprogramação

---

# 🧠 Multiprogramação

Na multiprogramação, **vários programas podem permanecer na memória ao mesmo tempo**.

```text
┌─────────────────────────┐
│       💾 MEMÓRIA        │
├─────────────────────────┤
│ 🟦 Programa A           │
├─────────────────────────┤
│ 🟩 Programa B           │
├─────────────────────────┤
│ 🟥 Programa C           │
└─────────────────────────┘
             │
             ▼
           🧠 CPU
```

## 🤔 Por que isso era necessário?

Imagine:

```text
Programa A
    │
    ▼
💽 Esperando I/O
```

Se só existisse um programa:

```text
🧠 CPU → 😴 PARADA
```

A CPU ficaria sem fazer nada enquanto o programa esperava o disco ou outro dispositivo.

Com multiprogramação:

```text
Programa A
    │
    ├──→ 💽 esperando I/O
    │
    ▼
Programa B
    │
    └──→ 🧠 usa a CPU
```

Depois:

```text
A espera I/O
     ↓
B usa CPU
     ↓
B espera I/O
     ↓
C usa CPU
```

### 🎯 Resultado

A CPU passa a ser utilizada de forma muito mais eficiente.

```text
SEM MULTIPROGRAMAÇÃO

CPU:
██████░░░░░░░░░░░░████


COM MULTIPROGRAMAÇÃO

CPU:
██████████████████████
```

> ⭐ **Ideia fundamental:** quando um programa está esperando uma operação de I/O, a CPU pode executar outro programa.

---

# 🧩 Comparando as três primeiras gerações

|                   | 🔥 1ª                        | ⚡ 2ª                | 🔬 3ª                      |
| ----------------- | ---------------------------- | ------------------- | -------------------------- |
| 📅 Período        | 1945–1955                    | 1955–1965           | 1965–1980                  |
| 💻 Hardware       | Válvulas                     | Transistores        | Circuitos integrados       |
| ⚙️ Característica | Programação direta           | Sistemas em lote    | Multiprogramação           |
| 👨‍💻 Interação   | Muito manual                 | Mais automatizada   | Sistemas mais sofisticados |
| 🎯 Objetivo       | Fazer o computador funcionar | Reduzir desperdício | Aumentar utilização da CPU |

---

# 🧠 Evolução em uma imagem

```text
🔥 1ª GERAÇÃO
VÁLVULAS
   │
   │ computadores enormes
   │ programação direta
   ▼
⚡ 2ª GERAÇÃO
TRANSISTORES
   │
   │ maior confiabilidade
   │ processamento em lote
   ▼
🔬 3ª GERAÇÃO
CIRCUITOS INTEGRADOS
   │
   │ computadores mais poderosos
   │ multiprogramação
   ▼
🧠 USO MAIS EFICIENTE DA CPU
```

---

# 🎯 O que memorizar para a prova

### ⭐ 1. Primeira geração

> **Válvulas → programação direta**

### ⭐ 2. Segunda geração

> **Transistores → processamento em lote**

### ⭐ 3. Terceira geração

> **Circuitos integrados → multiprogramação**

---

## 🧠 Macete para decorar

### **🔥 → ⚡ → 🔬**

```text
🔥 Válvula
   ↓
⚡ Transistor
   ↓
🔬 Circuito Integrado
```

Associe cada uma à sua principal característica:

```text
🔥 Válvulas
   → 👨‍💻 Programação direta

⚡ Transistores
   → 📦 Batch

🔬 Circuitos Integrados
   → 🧠 Multiprogramação
```

### 💡 Frase para decorar:

> **"Válvula programa, transistor agrupa, circuito integrado multiprograma."**

---

# 📝 Resumo final

A evolução dos sistemas operacionais acompanhou a evolução do hardware.

Na **primeira geração (1945–1955)**, os computadores utilizavam **válvulas** e eram programados de forma muito direta.

Na **segunda geração (1955–1965)**, os **transistores** tornaram os computadores menores, mais rápidos e confiáveis. Surgiram os **sistemas em lote**, permitindo executar vários trabalhos em sequência.

Na **terceira geração (1965–1980)**, os **circuitos integrados** aumentaram ainda mais a capacidade dos computadores. Surgiu a **multiprogramação**, permitindo manter vários programas na memória e utilizar a CPU enquanto outro programa aguardava uma operação de entrada/saída.

---

# 🚀 TL;DR

```text
🔥 1945–1955
Válvulas
→ programação direta

⚡ 1955–1965
Transistores
→ Batch

🔬 1965–1980
Circuitos Integrados
→ Multiprogramação
```

> ## 🎯 Se você lembrar dessa sequência, já terá a espinha dorsal da história dos SOs:
>
> **VÁLVULAS → TRANSISTORES → CIRCUITOS INTEGRADOS**
>
> **DIRETO → BATCH → MULTIPROGRAMAÇÃO**

```
```
