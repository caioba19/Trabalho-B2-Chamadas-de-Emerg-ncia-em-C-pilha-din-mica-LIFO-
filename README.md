# Trabalho B2 – Chamadas de Emergência

Implementação de uma **pilha dinâmica encadeada (LIFO)** em linguagem C, simulando um sistema de registro e atendimento de chamadas de emergência.

Trabalho prático da disciplina **Estruturas de Dados** – 2026.1  
Linguagem: C (padrão C99)  
Repositório do professor: [NirtonAfonso/Trabalho-Estruturas-de-Dados-2026](https://github.com/NirtonAfonso/Trabalho-Estruturas-de-Dados-2026)

---

## Sobre o Tema

Neste sistema, cada chamada registrada é empilhada no topo. A última chamada registrada será a primeira a ser atendida, respeitando o comportamento **LIFO** (*Last In, First Out*).

---

## Estrutura de Dados

Cada chamada armazena os seguintes campos:

| Campo       | Tipo       | Descrição                    |
|-------------|------------|------------------------------|
| `protocolo` | `int`      | Identificador único          |
| `local`     | `char[50]` | Local da emergência          |
| `tipo`      | `char[30]` | Tipo da ocorrência           |
| `horario`   | `char[20]` | Horário da chamada (HH:MM)   |

A pilha é composta por nós alocados dinamicamente com `malloc` e liberados com `free`. Nenhum vetor estático é utilizado.

---

## Funcionalidades

| Opção | Operação     | Descrição                                          |
|-------|--------------|----------------------------------------------------|
| 1     | Push         | Registra nova chamada no topo da pilha             |
| 2     | Pop          | Atende e remove a chamada do topo                  |
| 3     | Peek         | Consulta a próxima chamada sem remover             |
| 4     | Listar       | Exibe todas as chamadas do topo até a base         |
| 5     | Salvar CSV   | Grava os dados atuais em `chamadas.csv`            |
| 6     | Carregar CSV | Recarrega os dados do arquivo para a pilha         |
| 0     | Sair         | Salva automaticamente e encerra o programa         |

---

## Como Compilar e Executar

### Pré-requisito

Ter o GCC instalado. Para verificar:

```bash
gcc --version
```

Caso não tenha, instale via:

- **Linux/Ubuntu:** `sudo apt install gcc`
- **Windows:** instale o [MinGW](https://www.mingw-w64.org/) ou use o CodeBlocks

### Compilar

```bash
gcc -o pilha_emergencia pilha_emergencia.c -std=c99
```

### Executar

```bash
./pilha_emergencia
```

> No Windows, use `pilha_emergencia.exe`

---

## Persistência de Dados

O programa salva e carrega automaticamente o arquivo `chamadas.csv`, criado na mesma pasta do executável.

Formato do arquivo:

```
protocolo;local;tipo;horario
1001;Av. Paulista;Acidente;14:30
1002;Rua das Flores;Incendio;14:35
```

Ao iniciar, o programa tenta carregar o CSV automaticamente. Ao sair (opção 0), os dados são salvos automaticamente.

---

## Exemplo de Uso

```
Registrar protocolo 1001 → Push
Registrar protocolo 1002 → Push
Consultar topo           → Peek  → exibe 1002
Atender                  → Pop   → remove 1002
Atender                  → Pop   → remove 1001
Atender                  → Pop   → pilha vazia
```

---

## Validações Implementadas

- Protocolo duplicado é rejeitado
- Protocolo deve ser um número positivo
- Campos vazios (local, tipo, horário) são rejeitados
- Pop e Peek avisam quando a pilha está vazia
- Toda memória alocada é liberada antes de encerrar

---

## Autores

**Caio Vinicius , Daniel oliveira , João Pedro Gonzaga, Maicon Dias e Yuri Sales**  
Sistemas de Análise e Desenvolvimento – UniJorge  
