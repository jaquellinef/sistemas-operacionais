# Capítulo 7 — Virtualização e Computação em Nuvem

> **Guia introdutório baseado nos conceitos do Capítulo 7 de _Modern Operating Systems_, de Andrew S. Tanenbaum e Herbert Bos.**
>
> Este material foi escrito com linguagem própria e didática. Ele serve como apoio para estudo e não reproduz o texto do livro.

---

# Sumário

1. [Introdução](#1-introdução)
2. [O que é virtualização?](#2-o-que-é-virtualização)
3. [Por que usar virtualização?](#3-por-que-usar-virtualização)
4. [Máquinas virtuais](#4-máquinas-virtuais)
5. [O que é um hipervisor?](#5-o-que-é-um-hipervisor)
6. [Hipervisores Tipo 1 e Tipo 2](#6-hipervisores-tipo-1-e-tipo-2)
7. [Host e Guest](#7-host-e-guest)
8. [O desafio da virtualização](#8-o-desafio-da-virtualização)
9. [Privilégios e proteção](#9-privilégios-e-proteção)
10. [Virtualização assistida por hardware](#10-virtualização-assistida-por-hardware)
11. [Virtualização de CPU](#11-virtualização-de-cpu)
12. [Virtualização de memória](#12-virtualização-de-memória)
13. [Virtualização de entrada e saída](#13-virtualização-de-entrada-e-saída)
14. [Discos virtuais](#14-discos-virtuais)
15. [Rede virtual](#15-rede-virtual)
16. [Virtual Appliances](#16-virtual-appliances)
17. [Máquinas virtuais em processadores multicore](#17-máquinas-virtuais-em-processadores-multicore)
18. [Virtualização e desempenho](#18-virtualização-e-desempenho)
19. [Virtualização e segurança](#19-virtualização-e-segurança)
20. [Virtualização x emulação](#20-virtualização-x-emulação)
21. [Computação em nuvem](#21-computação-em-nuvem)
22. [IaaS, PaaS e SaaS](#22-iaas-paas-e-saas)
23. [Data centers e nuvem](#23-data-centers-e-nuvem)
24. [Migração de máquinas virtuais](#24-migração-de-máquinas-virtuais)
25. [Migração ao vivo](#25-migração-ao-vivo)
26. [Checkpoint](#26-checkpoint)
27. [VMware como estudo de caso](#27-vmware-como-estudo-de-caso)
28. [Vantagens da virtualização](#28-vantagens-da-virtualização)
29. [Desvantagens e desafios](#29-desvantagens-e-desafios)
30. [Exemplo completo](#30-exemplo-completo)
31. [Mapa mental](#31-mapa-mental)
32. [Resumo para prova](#32-resumo-para-prova)
33. [Perguntas para revisar](#33-perguntas-para-revisar)
34. [Conclusão](#34-conclusão)
35. [Glossário](#35-glossário)

---

# 1. Introdução

Para entender este capítulo, primeiro precisamos entender uma ideia muito simples:

> **Um computador possui recursos físicos que podem ser compartilhados entre diferentes sistemas e programas.**

Entre esses recursos estão:

- CPU;
- memória RAM;
- armazenamento;
- placa de rede;
- dispositivos de entrada e saída.

Normalmente temos uma estrutura parecida com esta:

```text
┌──────────────────────────────┐
│          APLICAÇÕES          │
│ Navegador, jogos, editores...│
├──────────────────────────────┤
│      SISTEMA OPERACIONAL     │
│      Windows / Linux         │
├──────────────────────────────┤
│          HARDWARE            │
│ CPU / RAM / SSD / Rede       │
└──────────────────────────────┘
