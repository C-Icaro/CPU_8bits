# 🧠 CPU SAP-1 Simplificada  
Ring Counter + Tri-State Bus  
Simulação no Digital (HNeemann)

---

## 📌 Visão Geral

Este projeto consiste na implementação de uma CPU simplificada inspirada na arquitetura SAP-1 (Simple As Possible), utilizando:

- Ring Counter para controle de ciclos
- Barramento compartilhado com drivers tri-state
- Memória RAM baseada em EEPROM
- Registradores fundamentais (PC, MAR, IR, etc.)
- ALU de 8 bits previamente desenvolvida

A CPU foi projetada e simulada no software Digital, de HNeemann, com foco em:

- Clareza arquitetural  
- Modularidade  
- Fidelidade conceitual aos fundamentos de computação  

---

## 🎯 Objetivo

Construir e compreender, na prática, o funcionamento interno de uma CPU básica, incluindo:

- Ciclo de Busca (Fetch)  
- Ciclo de Execução (Execute)  
- Comunicação entre módulos via barramento compartilhado  
- Controle temporal via ring counter

---

## 🧱 Arquitetura Geral

A CPU é composta pelos seguintes blocos principais:

### 🔁 Unidade de Controle
- Implementada com Ring Counter
- Gera sinais temporais: `T1, T2, T3, ...`
- Controla toda a sequência de execução

### 📍 Program Counter (PC)
- Armazena o endereço da próxima instrução
- Pode:
  - Incrementar
  - Enviar valor para o barramento

### 📦 MAR (Memory Address Register)
- Recebe endereço do barramento
- Endereça a memória

### 🧠 Memória (RAM 16x2)
- Implementada com EEPROM
- Separação em:
  - Parte baixa (BUS_LOW)
  - Parte alta (BUS_HIGH)

### 🧮 ALU (8 bits)
- Responsável pelas operações aritméticas e lógicas

### 🔌 Barramento (BUS)
- Compartilhado entre todos os módulos
- Controlado via tri-state drivers
- Evita conflitos (apenas um módulo escreve por vez)

---

## ⚙️ Funcionamento

### 🔄 Ciclo de Busca (Fetch)

| Tempo | Operação |
|------|--------|
| T1 | PC → BUS |
| T2 | BUS → MAR |
| T3 | RAM → BUS |
| T4 | BUS → IR |

---

### ⚡ Ciclo de Execução (Execute)

Depende da instrução, mas segue o padrão:

- Decodificação da instrução (IR)
- Ativação de sinais de controle
- Uso da ALU, registradores ou memória

---

## 🧩 Principais Decisões de Projeto

### 🧵 Uso de Tri-State Bus
- Permite múltiplos dispositivos conectados ao mesmo barramento
- Apenas um dispositivo escreve por vez
- Evita necessidade de múltiplos multiplexadores

### 🔁 Uso de Ring Counter
- Simplifica o controle sequencial
- Substitui lógica complexa de controle
- Cada estado ativa uma etapa do ciclo

### 🧠 Separação da Memória (HIGH/LOW)
- Facilita manipulação de dados em 8 bits
- Permite debug visual mais claro

---

## 🧪 Testes Realizados

- Verificação do ciclo completo de fetch  
- Testes com diferentes valores na RAM  
- Validação do fluxo PC → MAR → RAM → IR  
- Debug através de sinais intermediários (`DEBUG_*`)

---

## 📚 Referência Teórica

Este projeto foi fortemente baseado no livro:

> Digital Computer Electronics – Albert Paul Malvino

O livro serviu como principal base para:

- Estrutura da arquitetura SAP-1  
- Organização dos ciclos de instrução  
- Conceitos de barramento, registradores e controle  
- Modelagem didática de CPUs simples  

A implementação buscou manter fidelidade aos conceitos apresentados, adaptando-os para o ambiente de simulação digital.

---

## 🎥 Vídeo Explicativo

📎 Link do YouTube:  [Link](https://youtu.be/l2msdoqcu7w)

---

## 🛠️ Ferramentas Utilizadas

- Digital (HNeemann)  
- Conhecimentos de lógica digital  
- Arquitetura de computadores  
- Modelagem de sistemas  

---

## 🚀 Possíveis Extensões

- Implementação de mais instruções  
- Adição de registradores auxiliares  
- Implementação de pipeline simples  
- Integração com interface de entrada/saída  
- Implementação de unidade de controle microprogramada  

---

## 👨‍💻 Autor

Projeto desenvolvido como parte da disciplina de arquitetura/computação digital, com foco em aprendizado prático e aprofundamento conceitual.
