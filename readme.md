# 🎓 Aula 01 - Apresentação da Disciplina e Introdução aos Sistemas Operacionais

👨‍🏫 **Professor:** Prof. Me. Deivison S. Takatu  
📧 **E-mail:** deivison.takatu@fatec.sp.gov.br  

---

## 👥 Apresentação da Turma
- 💼 Experiências profissionais na área  
- 🎯 Expectativas após a conclusão do curso  
- 🎨 Um hobby ou passatempo  

---

## 📑 Sumário
1️⃣ Apresentação da Disciplina e Contextualização  
2️⃣ Plano de Aulas e Ensino  
3️⃣ Contexto da Disciplina  
4️⃣ Sequência dos Conteúdos do Semestre  
5️⃣ Metodologia de Ensino  
6️⃣ Critérios de Avaliação  
7️⃣ Atividade  
8️⃣ Conclusão  

---

## 🎓 Histórico Acadêmico e Profissional

| Formação | Ano |
|----------|-----|
| Mestre em Ciência da Computação | 2021 |
| Especialização em Inteligência Artificial | Atual |
| 4 Pós-graduações Lato sensu | - |
| Graduação em ADS | 2016 |

| Experiência Profissional | Período |
|--------------------------|---------|
| Gerente de Projetos | 2023 - Atual |
| Professor Universitário | 2022 - Atual |
| Coordenador Acadêmico | 2019 - 2021 |
| Professor de Informática | 2017 - 2023 |

---

## 🏫 Atuação na FATEC
- 💻 Orientações: Programação Web  
- 📊 Projetos: Programação Web e Educação Financeira  

---

## 💻 O Que São Sistemas Operacionais?
- 📌 **Definição:** Software essencial que gerencia hardware e software  
- 🔑 **Importância:** Interface entre usuário e máquina  
- 🖥️ **Exemplos:** Windows, macOS, Linux, Android, iOS  

---

## ⚙️ Estrutura Interna: Camadas e Modelos
- 🧩 **Estrutura em Camadas:** Organização hierárquica para modularidade  
- 🏗️ **Monolítica vs. Modular:** Diferentes abordagens de design de kernel  
- 🔧 **Kernel:** Núcleo do SO, acesso direto ao hardware, gerenciamento de recursos vitais  
- 🔒 **Modos de Operação:**  
  - 👤 Modo Usuário: Programas comuns  
  - 🛡️ Modo Kernel: Privilégios elevados, acesso total  

---
## Fluxograma do Kernel
```mermaid
flowchart TD
    A[Usuário] --> B[Modo Usuário]
    B --> C[Chamadas de Sistema]
    C --> D[Kernel]
    D --> E[Gerenciamento de Processos]
    D --> F[Gerenciamento de Memória]
    D --> G[Gerenciamento de Dispositivos]
    E --> H[Hardware]
    F --> H
    G --> H
---
## ⏱️ Escalonamento de Processos
**Objetivo:** decidir qual processo executar e por quanto tempo para otimizar eficiência, justiça e tempo de resposta.

| **Algoritmo** | **Resumo** | **Uso típico** |
|---------------|------------|----------------|
| FIFO          | Primeiro a entrar, primeiro a sair | Batch |
| Round Robin   | Fatias de tempo (quantum)          | Interativo |
| Prioridade    | Executa por prioridade; envelhecimento evita inanição | Sistemas com níveis de serviço |

### Fluxograma de Escalonamento

```mermaid
flowchart LR
  P[Processos prontos] -->|FIFO| F[FIFO Queue]
  P -->|Round Robin| R[Round Robin Queue]
  P -->|Prioridade| Pr[Priority Queue]
  F --> Exec[Execução]
  R --> Exec
  Pr --> Exec
  Exec --> Resultado[Saída / Espera / I/O]

---

## 🧠 Gerenciamento de Memória — Real e Virtual

### Memória Principal
- Alocação dinâmica  
- Proteção entre processos  
- Compartilhamento controlado quando necessário  

### Memória Virtual
- Paginação e segmentação  
- TLB (Translation Lookaside Buffer)  
- Swap / Pagefile  

**Resumo:**  
A memória virtual permite endereçamento lógico maior que a RAM física, melhora o isolamento entre processos e possibilita execução de programas maiores. Porém, pode causar overhead quando há muito swapping.


## 🔌 Dispositivos, Sistemas de Arquivos e Futuro

### Gerenciamento de E/S
- Abstração de dispositivos via drivers  
- Tratamento de interrupções  
- Buffering  
- Filas de E/S  
- DMA (Direct Memory Access)  

### Sistemas de Arquivos
| **Sistema** | **Pontos fortes** | **Uso típico** |
|-------------|-------------------|----------------|
| ext4        | Estável, journaling | Linux |
| NTFS        | Permissões avançadas, compressão | Windows |
| FAT32/exFAT | Compatibilidade entre diferentes SOs | Dispositivos removíveis |
| XFS/ZFS     | Escalabilidade, integridade | Storage corporativo |

## 🔒 Segurança e Virtualização

### Segurança
- Autenticação  
- Autorização  
- Controle de acesso  
- Criptografia  
- Atualizações e hardening  

### Virtualização
- Hipervisores (tipo 1 e tipo 2)  
- Containers (ex.: Docker)  
- Orquestração (ex.: Kubernetes)  

### Tendências Futuras
- NFV (Network Function Virtualization)  
- Serverless na borda  
- Isolamento por hardware (SGX, TrustZone)  
- Sistemas Operacionais otimizados para IoT e edge computing  

## 💡 Dica importante — Portfólio de Projetos
**Por que:** demonstra habilidades práticas, criatividade e domínio de ferramentas; facilita avaliação e oportunidades profissionais.  

**O que incluir:**
- README claro e objetivo  
- Instruções de execução  
- Código organizado  
- Documentação técnica  
- Licença  
- Histórico de commits  

---

## 📊 Critérios de Avaliação

**Fórmula da nota final**



\[
\textbf{Nota Final} = (P1 \cdot 0.25) + (P2 \cdot 0.25) + ((PJ + AT) \cdot 0.25)
\]



**Componentes**
- **P1 — Prova 1:** 25%  
- **P2 — Prova 2:** 25%  
- **PJ — Projeto:** 25%  
- **AT — Atividades:** 25%  

**Rubrica sugerida para Projeto (PJ)**
- Funcionalidade: 40%  
- Documentação: 20%  
- Qualidade do Código: 20%  
- Apresentação: 20%  

---

## 📝 Atividades e Entregas
- **Formação de grupos** — criar `grupo.md` com nomes completos, RA/matrícula e e‑mail.  
- **Repositório GitHub** — incluir `README.md` e `Aula01.md`.  
- **Mapa mental (Miro)** — linha do tempo dos SOs; exportar para `.md` ou imagem; salvar no repositório.  
- **Projeto (PJ)** — entregas parciais e entrega final com documentação e demonstração.  




