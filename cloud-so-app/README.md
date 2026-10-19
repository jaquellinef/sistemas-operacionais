# 💻 cloud-so-app — Painel de Monitoramento do Sistema Operacional

[![Node.js](https://img.shields.io/badge/Node.js-v24.x-339933?style=flat-square&logo=node.js)](https://nodejs.org/)
[![Express.js](https://img.shields.io/badge/Express.js-v4.x-000000?style=flat-square&logo=express)](https://expressjs.com/)
[![Render](https://img.shields.io/badge/Deploy-Render-46E3B7?style=flat-square&logo=render)](https://cloud-so-app-jaque.onrender.com)
[![Railway](https://img.shields.io/badge/Deploy-Railway-0B0D0E?style=flat-square&logo=railway)](https://sistemas-operacionais-production.up.railway.app)

**Aplicação:** `cloud-so-app`  
**Autora:** Jaquelline ([@jaquellinef](https://github.com/jaquellinef))  
**Repositório:** [github.com/jaquellinef/cloud-so-app](https://github.com/jaquellinef/cloud-so-app)  
**Ambiente Cloud (Render):** [cloud-so-app-jaque.onrender.com](https://cloud-so-app-jaque.onrender.com)  
**Ambiente Cloud (Railway):** [sistemas-operacionais-production.up.railway.app](https://sistemas-operacionais-production.up.railway.app)  

---

## 📋 Sumário

- [1. Sobre o Projeto](#1-sobre-o-projeto)
- [2. Funcionalidades](#2-funcionalidades)
- [3. Tecnologias Utilizadas](#3-tecnologias-utilizadas)
- [4. Estrutura do Projeto](#4-estrutura-do-projeto)
- [5. Como Executar Localmente](#5-como-executar-localmente)
- [6. Implantação e Hospedagem na Nuvem (PaaS)](#6-implantação-e-hospedagem-na-nuvem-paas)
  - [6.1. Render](#61-render)
  - [6.2. Railway](#62-railway)
- [7. Análise Comparativa de Ambientes](#7-análise-comparativa-de-ambientes)
- [8. Conceitos de Sistemas Operacionais Aplicados](#8-conceitos-de-sistemas-operacionais-aplicados)
- [9. Solução de Problemas Enfrentados](#9-solução-de-problemas-enfrentados)
- [10. Autora](#10-autora)

---

## 1. Sobre o Projeto

O **`cloud-so-app`** é uma aplicação web desenvolvida em JavaScript/Node.js com o framework **Express.js**, com a finalidade de coletar, analisar e monitorar métricas em tempo real do Sistema Operacional e do Hardware do ambiente onde está sendo executada (máquina local ou instâncias de contêineres em nuvem).

O projeto atua como estudo prático sobre o funcionamento de **Sistemas Operacionais**, demonstrando conceitos fundamentais como chamadas de sistema (*sys calls*), gerenciamento de processos (PCB/TCB), alocação de memória física/virtual, escalonamento de CPU e virtualização/conteinerização sob modelos **PaaS (Plataforma como Serviço)**.

---

## 2. Funcionalidades

- **Coleta de Métricas de Hardware e SO em Tempo Real:**
  - Identificação de **Hostname** e identificadores de contêiner.
  - Identificação da **Plataforma (SO)**, do **Kernel** e da **Arquitetura** (`x64`).
  - Mapeamento detalhado dos **Núcleos e Modelo da CPU**.
  - Monitoramento de **Memória RAM Total** e **Memória RAM Livre** (com conversão para GB).
  - Cálculo do **Tempo de Atividade (Uptime)** do sistema em horas ou dias.
- **Interface Web Responsiva:**
  - Painel visual estilizado renderizado no lado do servidor.
- **Suporte Multi-Ambiente:**
  - Compatibilidade com Windows (ambiente local) e Linux (contêineres Docker/LXC na nuvem).

---

## 3. Tecnologias Utilizadas

- **Linguagem & Runtime:** Node.js (v24.x LTS)
- **Framework Web:** Express.js
- **Módulos Nativos:** `os` (Interface direta com o SO)
- **Controle de Versão:** Git e GitHub
- **Hospedagem / Cloud PaaS:** Render e Railway
- **Virtualização & Contêineres:** Docker / LXC

---

## 4. Estrutura do Projeto

```text
cloud-so-app/
├── node_modules/        # Dependências do projeto (Express)
├── .gitignore          # Regras para ignorar arquivos não versionados (node_modules)
├── package.json        # Manifesto do projeto e dependências Node.js
├── package-lock.json   # Mapeamento exato de versões
├── server.js           # Ponto de entrada principal e lógica da aplicação
├── MANUAL.md           # Manual de desenvolvimento e conceitos de SO
├── Relatório_Atividade_07.md  # Relatório de implantação em provedores PaaS
├── README.md           # Documentação geral do repositório
├── metrica_jaque.jpg   # Captura da execução local (Windows)
├── metrica_render.jpg  # Captura de métricas no Render
├── tela_render.jpg     # Painel de controle do Render
├── tela_projeto_railway.png   # Configuração do projeto no Railway
└── Captura de tela 2026-10-06 _railway.png  # Configurações de rede do Railway
```

---

## 5. Como Executar Localmente

### Pré-requisitos
- **Node.js** (v18.x ou superior) instalado (`node -v`).
- **Git** instalado (`git --version`).

### Passo a Passo

1. **Clonar o repositório:**
   ```bash
   git clone https://github.com/jaquellinef/cloud-so-app.git
   cd cloud-so-app
   ```

2. **Instalar as dependências:**
   ```bash
   npm install
   ```

3. **Iniciar a aplicação:**
   ```bash
   node server.js
   ```

4. **Acessar no navegador:**
   Abra o endereço `http://localhost:3000` para visualizar o painel com as métricas da sua máquina local.

---

## 6. Implantação e Hospedagem na Nuvem (PaaS)

A aplicação foi implantada e testada em dois provedores de Plataforma como Serviço (**PaaS**): **Render** e **Railway**.

### 6.1. Render

- **URL Pública:** `https://cloud-so-app-jaque.onrender.com` / `https://cloud-so-app-6elo.onrender.com`
- **Configuração:**
  - **Runtime:** Node
  - **Build Command:** `npm install`
  - **Start Command:** `node server.js`
  - **Plataforma:** Linux (`x64`), Kernel `aws`
- **Comportamento:** A aplicação executa isolada dentro de um contêiner Linux, reportando especificações do nó hospedeiro do cluster do provedor.

### 6.2. Railway

- **URL Pública:** `sistemas-operacionais-production.up.railway.app`
- **Configuração:**
  - **Conexão:** Repositório do GitHub (`jaquellinef/sistemas-operacionais`)
  - **Diretório Raiz:** `/cloud-so-app`
  - **Porta do Contêiner:** `8080` (atribuída dinamicamente)
  - **Isolamento:** Contêiner Docker / LXC Linux
- **Desempenho:** Instância vinculada a host multicore de alto desempenho (48 vCPUs e mais de 300 GB de RAM compartilhada).

---

## 7. Análise Comparativa de Ambientes

A tabela abaixo compila os dados coletados diretamente em execução nos três ambientes de teste:

| Métrica / Parâmetro | Execução Local (Máquina Física) | Nuvem — Render (PaaS) | Nuvem — Railway (PaaS) |
| :--- | :--- | :--- | :--- |
| **Ambiente** | Windows 11 (Físico) | Linux (Contêiner AWS) | Linux (Contêiner LXC/Docker) |
| **Hostname** | `Jaquelline` | `srv-daug...` / `srv-db2...` | `5f456ede1912` |
| **Plataforma (SO)** | `win32` | `linux` | `linux` |
| **Arquitetura** | `x64` | `x64` | `x64` |
| **Processador (CPU)** | 12x Intel(R) Core(TM) i5-1235U | 8x AMD EPYC 7R13 Processor | 48x AMD EPYC 9655 96-Core |
| **Memória RAM Total** | `7.73 GB` | `30.65 GB` | `322.69 GB` |
| **Memória RAM Livre** | `0.75 GB` | `8.53 GB` a `11.86 GB` | `89.33 GB` |
| **Uptime (Atividade)**| ~7 dias (173h) | ~159 dias (3816h) | ~151 dias (3630h) |

---

## 8. Conceitos de Sistemas Operacionais Aplicados

1. **Processos e Bloco de Controle de Processo (PCB):**  
   Quando o comando `node server.js` é executado, o SO cria um novo processo, atribui um **PID (Process ID)** único e aloca uma estrutura **PCB/TCB** no Kernel para gerenciar estado, registradores e ponteiros de memória do runtime Node.js.

2. **Chamadas de Sistema (*System Calls*):**  
   Métodos nativos como `os.freemem()`, `os.totalmem()`, `os.cpus()` e `os.uptime()` realizam chamadas de sistema (*sys calls*) ao Kernel do SO hospedeiro para ler as estruturas da tabela de processos e da memória física.

3. **Gerenciamento de Memória e Coleta de Lixo (V8 GC):**  
   A aplicação utiliza a Engine V8 do Node.js, que gerencia a memória em *Heap* e *Stack*, acionando o *Garbage Collector* periodicamente no espaço de usuário (*User Space*).

4. **Escalonamento de Processos (Scheduler):**  
   O escalonador do Kernel (seja no Windows ou no Linux) alterna a execução dos threads do Node.js/V8 entre os núcleos de CPU disponíveis (Intel i5 no ambiente local e AMD EPYC na nuvem).

5. **Virtualização e Conteinerização:**  
   Em ambientes PaaS (Render e Railway), a aplicação roda de forma isolada através de contêineres. O *hostname* reportado é a ID do contêiner, e os recursos de CPU/RAM expostos pelo módulo `os` refletem o nó físico da infraestrutura de nuvem, demonstrando a abstração fornecida pela virtualização.

---

## 9. Solução de Problemas Enfrentados

- **Erro de Extensão de Arquivo (`MODULE_NOT_FOUND`):**  
  *Sintoma:* O Node.js não encontrou o arquivo de inicialização local.  
  *Causa:* O sistema Windows salvou o arquivo como `server.js.txt`.  
  *Solução:* Renomeação direta do arquivo para `server.js` na raiz do projeto.

- **Bloqueio de E-mail Privado no GitHub (`GH007`):**  
  *Sintoma:* O comando `git push` falhou devido às regras de e-mail privado do GitHub.  
  *Solução:* Ajuste nas configurações de e-mail da conta no GitHub (`settings/emails`), desativando o bloqueio de envios por linha de comando.

---

## 10. Autora

Desenvolvido por **Jaquelline**  
- **GitHub:** [@jaquellinef](https://github.com/jaquellinef)  
- **Projeto:** `cloud-so-app`  

---
