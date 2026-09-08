# Manual de Instalação, Configuração e Testes: Tiny Core Linux no Oracle VirtualBox

> **Disciplina:** Sistemas Operacionais / Infraestrutura de TI  
> **Autor:** Jaquelline Feitoza 
> **Data:** 11/09/2026 
> **Repositório:** [Atividade5/Link do Repositório]

---

## 1. Introdução

Este relatório documenta o processo prático de instalação, virtualização e teste do sistema operacional **Tiny Core Linux** utilizando a plataforma de virtualização **Oracle VM VirtualBox**. 

O Tiny Core Linux é uma distribuição altamente modular e minimalista de código aberto, projetada para rodar inteiramente na memória RAM do computador. O objetivo desta atividade é compreender o funcionamento de máquinas virtuais, gerenciar alocação de recursos de hardware e explorar um sistema operacional de baixo consumo de recursos.

---

## 2. Requisitos de Hardware e Software

* **Hypervisor:** Oracle VM VirtualBox (Versão 7.0 ou superior).
* **Imagem ISO:** Tiny Core Linux (`CorePlus-current.iso` ou `TinyCore-current.iso`).
* **Recursos da VM Alocados:**
  * **Processador:** 1 vCPU.
  * **Memória RAM:** 512 MB (256 MB mínimo).
  * **Armazenamento:** 8 GB VDI (Alocado dinamicamente).
  * **Rede:** Placa em modo NAT.

---

## 3. Passo a Passo da Instalação e Configuração

### Etapa 1: Criação da Máquina Virtual

1. Abra o VirtualBox e clique em **Novo** (`Ctrl + N`).
2. Configure o nome da VM como `Tiny Core Linux`, defina o tipo como `Linux` e a versão como `Other Linux (64-bit)`.
3. Aloque **512 MB** de memória RAM.
4. Crie um novo disco rígido virtual do tipo **VDI (VirtualBox Disk Image)**, alocado dinamicamente com tamanho de **8 GB**.

![Criação da Máquina Virtual no VirtualBox](./prints/01_criacao_vm.png)
*Figura 1: Configuração dos parâmetros de hardware e resumo da criação da VM.*

---

### Etapa 2: Anexar a Imagem ISO

1. Acesse as **Configurações** da VM recém-criada (`Ctrl + S`).
2. Navegue até a seção **Armazenamento**.
3. Na controladora IDE, selecione o leitor de disco que se encontra **Vazio**.
4. No menu à direita, clique no ícone de disco e escolha o arquivo `.iso` baixado do Tiny Core Linux.
5. Confirme em **OK**.

![Montagem da ISO no VirtualBox](./prints/02_config_iso.png)
*Figura 2: Associação do arquivo ISO do Tiny Core ao leitor óptico virtual.*

---

### Etapa 3: Inicialização do Sistema (Live Mode)

1. Com a VM selecionada, clique em **Iniciar** (seta verde).
2. No menu do gerenciador de boot (*SYSLINUX*), pressione **Enter** na opção padrão de inicialização com interface gráfica.
3. Aguarde alguns segundos enquanto o sistema é carregado completamente na memória RAM.

![Menu de Boot do Tiny Core Linux](./prints/03_boot_menu.png)
*Figura 3: Menu de boot do Tiny Core Linux.*

![Ambiente de Trabalho FLWM](./prints/04_desktop_inicial.png)
*Figura 4: Interface gráfica minimalista (FLWM) do Tiny Core inicializada com sucesso.*

---

## 4. Testes e Exploração do Sistema

Foram realizados quatro testes práticos para avaliar a estabilidade, o consumo de recursos e a funcionalidade do ambiente virtualizado.

### Teste 1: Monitoramento de Hardware e Recursos (Terminal)
No terminal de comandos do Tiny Core, foram executados os comandos de checagem do sistema:

```bash
# Verificação do consumo de memória RAM
free -m

# Identificação da versão do Kernel e arquitetura
uname -a

# Informações do processador
cat /proc/cpuinfo | grep "model name"
