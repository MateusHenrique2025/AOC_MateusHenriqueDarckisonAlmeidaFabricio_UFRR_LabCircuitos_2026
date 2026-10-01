# AOC — Laboratório de Circuitos (Projeto Integrador)

**Subsistema de Memória e Unidade de Controle — Simulação em Logisim-Evolution**

| Campo | Informação |
|---|---|
| Disciplina | Arquitetura e Organização de Computadores |
| Curso | Ciência da Computação — Universidade Federal de Roraima (UFRR) |
| Semestre letivo | 2026.2 |
| Professor | Prof. Dr. Herbert Oliveira Rocha |
| Integrante 1 | [Fabrício Cauã Pereira Silvino] |
| Integrante 2 | [Mateus Henrique De Souza Pinheiro] |
| Integrante 3 | [Darckison Almeida Trajano]
| Repositório | `AOC_Nome1Nome2_UFRR_LabCircuitos_2026` |

---

## 1. Situação da entrega

| Parte | Descrição | Situação |
|---|---|---|
| Parte I | Módulo de memória de 64 bytes e cache de 4 linhas | Concluída. [com evidência] |
| Parte II | Unidade de controle cabeada e microprogramada | **Parcial** |

**Parte II — o que está pronto:** a unidade de controle cabeada (máquina de 5 estados com 3 flip-flops D e os 9 sinais de controle, só com portas AND, OR e NOT), com a sequência de estados e os sinais verificados no simulador, e o display do estado.

**Parte II — onde parou:** o caminho de dados está em montagem. Já existem o PC, a ROM de programa, o IR e os túneis dos sinais de controle; o multiplexador da entrada A da ULA está em andamento.

**Parte II — o que falta:** ULA e multiplexadores, `ULAOut`, banco de registradores, registradores A e B, extensor de sinal, a versão microprogramada (`parte2_microprogramada.circ`), o arquivo `microcodigo.txt`, a tabela de tempo exportada e os testes T-07, T-08 e T-09. O detalhamento está na Seção 0 do relatório técnico.

---

## 2. Ferramentas e como abrir os arquivos

- **Logisim-Evolution:** versão utilizada **5.0.0** (o enunciado pede 3.8.0 ou superior).
- **Planilha eletrônica:** [COMPLETAR: Calc, Excel ou Google Sheets] para `parte1_planilha.xlsx` e `tabela_tempo.xlsx`.
- **Git e GitHub:** controle de versão e entrega.

**Como abrir um arquivo `.circ`:** abra o Logisim-Evolution, use *Arquivo > Abrir* e selecione o arquivo. No painel da esquerda (*Design*), dê duplo clique no circuito desejado.

| Arquivo | Circuito a abrir | O que se vê |
|---|---|---|
| `parte1/parte1_memoria.circ` | [COMPLETAR: nome do circuito principal] | Módulo de memória de 64 bytes |
| `parte1/parte1_cache.circ` | [COMPLETAR: nome do circuito principal] | Cache de 4 linhas e contador de acertos |
| `parte2/parte2_cabeada.circ` | `JunMain` | Bloco `UC_cabeada` e o display do estado |
| `parte2/parte2_cabeada.circ` | `UC_cabeada` | Interior da unidade de controle (máquina de estados e sinais) |
| `parte2/parte2_cabeada.circ` | `CPU` | Caminho de dados em montagem (PC, ROM, IR) |

**Como simular a Parte II (`JunMain`):**

1. Em *Simular*, deixe os ticks automáticos desligados. O clock é um **pino manual**.
2. Coloque `RESET` em 1 e depois em 0. O estado vai para 0.
3. Cada pulso é `CLK` em 1 e depois em 0.
4. Com `B = 0` (tipo-R), a sequência é 0 → 1 → 2 → 3 → 0. Com `B = 1` (beq), é 0 → 1 → 4 → 0.

---

## 3. Estrutura do repositório e lista de arquivos

```
AOC_Nome1Nome2_UFRR_LabCircuitos_2026/
├── README.md
├── relatorio/relatorio_tecnico.pdf
├── parte1/
│   ├── parte1_memoria.circ
│   ├── parte1_cache.circ
│   ├── parte1_planilha.xlsx
│   └── evidencias/
├── parte2/
│   ├── parte2_cabeada.circ
└── componentes/
```

| Arquivo | Descrição | Situação |
|---|---|---|
| `README.md` | Este documento | Pronto |
| `relatorio/relatorio_tecnico.pdf` | Relatório técnico das duas partes | Parte II parcial; |
| `parte1/parte1_memoria.circ` | Módulo de memória de 64 bytes, decodificador 2→4, MUX de saída e erro de paridade |  |
| `parte1/parte1_cache.circ` | Cache de mapeamento direto, comparador de rótulos com XOR sintetizado e contador de acertos |  |
| `parte1/parte1_planilha.xlsx` | Traço de 16 acessos, indicadores (acertos, faltas, AMAT) e teste de conflito |  |
| `parte1/evidencias/` | Capturas de tela dos testes T-01 a T-05 |  |
| `parte2/parte2_cabeada.circ` | Unidade de controle cabeada (`UC_cabeada`), display do estado (`JunMain`) e caminho de dados parcial (`CPU`) | **Parcial** |
| `componentes/` | Arquivos `.circ` dos componentes reutilizados | |

---

## 4. Onde cada um dos dezessete componentes foi instanciado

[COMPLETAR: preencher a coluna "Subcircuito" para a Parte I e confirmar cada linha antes da entrega.]

| Nº | Componente | Parte | Arquivo | Subcircuito | Situação |
|---|---|---|---|---|---|
| 01 | Flip-flop D e JK | I e II | `parte2/parte2_cabeada.circ` | `UC_cabeada` (F2, F1, F0) | Parte II: concluído. |
| 02 | Multiplexador de 4 entradas | I e II | `parte2/parte2_cabeada.circ` | `CPU` | Parte II: parcial (mux da entrada A em andamento).  |
| 03 | XOR a partir de AND, NOT e OR | I | `parte1/parte1_cache.circ` |  |
| 04 | Somador de 8 bits com constante 4 | II | `parte2/parte2_cabeada.circ` | `CPU` | Pendente (hoje o PC + 4 é uma constante provisória) |
| 05 | Memória ROM de 8 bits | I e II | `parte2/parte2_cabeada.circ` | `CPU` (ROM 16×8 de programa) | Parte II: ROM de programa montada; ROM de microcódigo pendente.  |
| 06 | Memória RAM de 8 bits | I | `parte1/parte1_memoria.circ` | [COMPLETAR] | [COMPLETAR] |
| 07 | Banco de registradores de 8 bits | I e II | [COMPLETAR] | [COMPLETAR] | Parte II: pendente. 
| 09 | Detector da sequência "101" | II | [COMPLETAR] | [COMPLETAR] | [COMPLETAR: exercício preparatório] |
| 10 | ULA de 8 bits | II | — | — | Pendente |
| 11 | Extensor de sinal de 4 para 8 bits | II | — | — | Pendente |
| 12 | Máquina de estados com portas lógicas | II | `parte2/parte2_cabeada.circ` | `UC_cabeada` | Concluído |
| 13 | Contador síncrono (µPC de 3 bits) | II | — | — | Pendente |
| 14 | Detector de paridade ímpar | I | `parte1/parte1_memoria.circ` | |
| 15 | Otimização por mapas de Karnaugh | II | `relatorio/relatorio_tecnico.pdf` | Seção 3.5 | Concluído |
| 16 | Decodificador de 7 segmentos | I e II | `parte2/parte2_cabeada.circ` | `JunMain` | Parte II: parcial (usa o display hexadecimal da biblioteca; ver o relatório, Seção 9.2).  |
| 17 | Detector de número primo (4 bits) | I | `parte1/parte1_cache.circ` |  |

---

## 5. Declaração de uso de ferramentas de IA generativa

Foi utilizada a ferramenta **Claude (Anthropic)** nas seguintes etapas e finalidades:
- Etapas para Construção de cada componente;
- Ligações corretas de cada componente;
- Comportamento correto de cada circuito;
- Hierarquia correta dos arquivos;
- Problemas de sincronização;


Foi utilizada a ferramenta **Claude (Anthropic)** nas seguintes etapas e finalidades:

- explicação do enunciado da Parte II;
- conferência da derivação da tabela de transição, dos mapas de Karnaugh, das equações e do microprograma;
- orientação passo a passo da montagem no Logisim-Evolution;
- diagnóstico de erros a partir de capturas de tela (fios com larguras incompatíveis, túneis soltos, ordem dos bits no distribuidor);
- redação de rascunhos do relatório e deste README.

As decisões de projeto, a montagem dos circuitos e os testes foram executados pela equipe, que se responsabiliza por explicar o próprio circuito na arguição individual.

---

## 6. Divisão do trabalho

[COMPLETAR: descrever o que cada integrante fez. Todos os integrantes devem ter commits próprios no repositório.]

| Integrante | Responsabilidades |
|---|---|
| [Mateus Henrique De Souza Pinheiro] | [Parte II parcial] |
| [Fabrício Cauã Pereira Silvino] | [Parte I] |
| [Darckison Almeida Trajano] | Relatórios Parciais |
---

## 7. Limitações conhecidas

- A Parte II está incompleta (ver a Seção 1 e a Seção 0 do relatório). Os testes T-07, T-08 e T-09 **não foram realizados**, porque dependem do caminho de dados completo e da versão microprogramada.
- O formato da instrução de 8 bits (opcode, `rs`, `rt`, `rd`, imediato) não está definido no enunciado; por isso, a entrada `B` (1 = beq, 0 = tipo-R) é manual.
- O display do estado usa o display hexadecimal da biblioteca do Logisim. [COMPLETAR: reintegrar o decodificador próprio ou confirmar com o professor se a biblioteca é aceita como Componente 16.]
- O teste T-06 está parcial: falta a captura no circuito `CPU` com o IR igual a `0x11` e o PC igual a `0x04`.
