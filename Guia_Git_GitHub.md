# 🚀 Guia Prático de Git e GitHub: Clonagem, Versionamento e Solução de Erros

Este manual contém os comandos essenciais para trabalhar com projetos no **Git** e **GitHub**, cobrindo o fluxo de trabalho diário, projetos de terceiros (clonagem e contribuição) e solução de erros comuns.

---

## 📑 Sumário

1. [Clonar um Repositório do GitHub](#1-clonar-um-repositório-do-github)
2. [Clonar Projetos de Outras Pessoas (Terceiros)](#2-clonar-projetos-de-outras-pessoas-terceiros)
   * [Cenário A: Apenas para Estudo/Testes Locais](#cenário-a-apenas-para-estudotestes-locais)
   * [Cenário B: Para Modificar e Ter Sua Própria Versão (Fork + Clone)](#cenário-b-para-modificar-e-ter-sua-própria-versão-fork--clone)
   * [Sincronizar seu Fork com o Repositório Original (`upstream`)](#sincronizar-seu-fork-com-o-repositório-original-upstream)
3. [Criar e Subir um Novo Projeto Local](#3-criar-e-subir-um-novo-projeto-local)
4. [Atualizar um Projeto Existente (Fluxo Diário)](#4-atualizar-um-projeto-existente-fluxo-diário)
5. [Guia de Solução de Erros Comuns](#5-guia-de-solução-de-erros-comuns)
   * [Erro 1: remote origin already exists](#erro-1-remote-origin-already-exists)
   * [Erro 2: non-fast-forward / updates were rejected](#erro-2-non-fast-forward--updates-were-rejected)
6. [Comandos de Verificação Úteis](#6-comandos-de-verificação-úteis)

---

## 1. Clonar um Repositório do GitHub

Se o repositório é seu ou você tem permissão de escrita nele:

```bash
# 1. Navegue até a pasta onde deseja salvar o projeto
cd C:\Users\jaque\OneDrive\Documentos\GitHub

# 2. Clone o repositório
git clone https://github.com/jaquellinef/cloud-so-app.git

# 3. Acesse a pasta do projeto clonado
cd cloud-so-app
```

---

## 2. Clonar Projetos de Outras Pessoas (Terceiros)

Quando você quer usar o código de outra pessoa ou projeto Open Source, existem **dois cenários** comuns:

### Cenário A: Apenas para Estudo/Testes Locais
Se você quer apenas **executar o código no seu computador** para aprender, testar ou usar localmente (sem enviar alterações de volta para o GitHub da pessoa):

```bash
# 1. Copie o URL HTTPS do repositório da pessoa no GitHub
git clone https://github.com/NOME-DO-USUARIO/NOME-DO-PROJETO.git

# 2. Entre na pasta baixada
cd NOME-DO-PROJETO

# 3. Instale as dependências (se for Node.js, por exemplo)
npm install
```
> **Nota:** Você poderá alterar o código localmente e rodar no seu computador, mas **não** conseguirá fazer `git push` direto para o GitHub do autor original sem permissão expressa dele.

---

### Cenário B: Para Modificar e Ter Sua Própria Versão (Fork + Clone)
Se você quer modificar o projeto, publicar as mudanças na sua própria conta do GitHub (`jaquellinef`) ou propor melhorias ao criador original (*Pull Request*):

1. **Faça o Fork no site do GitHub:**
   * Acesse a página do projeto da pessoa no navegador (ex: `https://github.com/autor-original/projeto-legal`).
   * No canto superior direito da página, clique no botão **Fork**.
   * O GitHub criará uma cópia completa desse repositório **dentro da sua conta** (`https://github.com/jaquellinef/projeto-legal`).

2. **Clone a SUA cópia (o seu Fork) no seu computador:**
   ```bash
   cd C:\Users\jaque\OneDrive\Documentos\GitHub
   git clone https://github.com/jaquellinef/projeto-legal.git
   cd projeto-legal
   ```

3. **Agora você pode editar, commitar e enviar para o SEU GitHub livremente:**
   ```bash
   git add .
   git commit -m "feat: minhas alterações no projeto"
   git push origin main
   ```

---

### Sincronizar seu Fork com o Repositório Original (`upstream`)
Se o dono original do projeto fizer atualizações e você quiser trazer essas novidades para a sua cópia:

```bash
# 1. Vincule o repositório do dono original como 'upstream' (faz isso apenas uma vez)
git remote add upstream https://github.com/autor-original/projeto-legal.git

# 2. Baixe e junte as novidades do autor original na sua branch local
git fetch upstream
git merge upstream/main

# 3. Envie o seu Fork atualizado para a sua conta no GitHub
git push origin main
```

---

## 3. Criar e Subir um Novo Projeto Local

Se você criou o projeto primeiro no seu computador e agora deseja enviá-lo para um repositório no GitHub (`jaquellinef`):

```bash
# 1. Acesse o diretório do seu projeto no terminal
cd C:\Users\jaque\OneDrive\Documentos\GitHub\cloud-so-app

# 2. Inicialize o repositório Git local
git init

# 3. Adicione todos os arquivos ao versionamento
git add .

# 4. Crie o primeiro commit
git commit -m "feat: commit inicial do projeto"

# 5. Renomeie a branch principal para 'main'
git branch -M main

# 6. Vincule o repositório local ao remoto no GitHub
git remote add origin https://github.com/jaquellinef/cloud-so-app.git

# 7. Envie os arquivos para o GitHub
git push -u origin main
```

---

## 4. Atualizar um Projeto Existente (Fluxo Diário)

Sempre que você alterar ou adicionar novos arquivos no projeto local e quiser enviar as atualizações:

```bash
# 1. Verifique quais arquivos foram modificados
git status

# 2. Adicione os arquivos alterados
git add .

# 3. Registre a alteração com um commit
git commit -m "refactor: separacao do servidor e interface na pasta public"

# 4. Envie as alterações para o GitHub
git push
```

---

## 5. Guia de Solução de Erros Comuns

### Erro 1: `remote origin already exists`

**Sintoma:**
```text
PS C:\...> git remote add origin https://github.com/jaquellinef/cloud-so-app.git
error: remote origin already exists.
```

**Causa:** O Git local já possui uma URL vinculada ao nome `origin`.

**Solução:** Atualize o endereço da `origin` existente utilizando o comando `set-url`:
```bash
git remote set-url origin https://github.com/jaquellinef/cloud-so-app.git
```

---

### Erro 2: `non-fast-forward / updates were rejected`

**Sintoma:**
```text
! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/jaquellinef/cloud-so-app.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart.
```

**Causa:** O repositório remoto no GitHub possui arquivos ou commits que ainda não existem no seu computador.

#### Opção A: Sincronizar e Unir (Recomendado)
Puxe as alterações do GitHub para a sua máquina antes de enviar as suas:
```bash
# Puxe as alterações e reorganize o histórico local
git pull origin main --rebase

# Envie novamente para o GitHub
git push -u origin main
```

*Nota: Caso as histórias não estejam relacionadas, use:*
```bash
git pull origin main --allow-unrelated-histories
```

#### Opção B: Forçar o Envio (Sobrescrever o GitHub)
Se você tem certeza de que deseja **substituir totalmente** o conteúdo do GitHub pelo código do seu computador local:
```bash
git push -u origin main --force
```

---

## 6. Comandos de Verificação Úteis

* **Verificar o status dos arquivos:**
  ```bash
  git status
  ```

* **Verificar URLs remotas configuradas (origin e upstream):**
  ```bash
  git remote -v
  ```

* **Ver o histórico resumido de commits:**
  ```bash
  git log --oneline
  ```

---
*Manual preparado para o fluxo de trabalho no repositório `jaquellinef/cloud-so-app`.*
