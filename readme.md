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

### Fluxograma do Kernel


###⏱️ Escalonamento de Processos
```mermaid
flowchart LR
  P[📋 Processos prontos] -->|FIFO| F[FIFO Queue]
  P -->|Round Robin| R[Round Robin Queue]
  P -->|Prioridade| Pr[Priority Queue]
  F --> Exec[▶️ Execução]
  R --> Exec
  Pr --> Exec
  Exec --> Resultado[✅ Saída / ⏳ Espera / 🔄 I/O]

## 🧠Gerenciamento de Memória — Real e Virtual
```mermaid
flowchart TD
  Proc[Processo solicita memória] --> MM[Gerenciador de Memória]
  MM -->|Espaço livre| Aloca[Aloca em RAM]
  MM -->|Sem espaço| Swap[Move páginas para Swap]
  Swap --> Aloca
  Aloca --> Exec[Processo em execução]
  Exec -->|Acesso| TLB[TLB consulta]
  TLB -->|Hit| MemFís[Endereço físico]
  TLB -->|Miss| PageTable[Consulta tabela de páginas] --> MemFís


