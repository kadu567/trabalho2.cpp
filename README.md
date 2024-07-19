# Projeto de Somador de 4 Bits com Arduino

## Índice

1. [Organização de Diretórios e Arquivos](#organização-de-diretórios-e-arquivos)
2. [Software Demonstration](#software-demonstration)
3. [Overview of Developed Features](#overview-of-developed-features)
4. [Overview of Future Activities](#overview-of-future-activities)
5. [Overview of Resolved and Pending Bugs](#overview-of-resolved-and-pending-bugs)
6. [Descrição do Código](#descrição-do-código)
7. [Como Usar](#como-usar)
8. [Licença](#licença)

---

## Demonstração de Software

### Introdução ao Software
“Este software foi desenvolvido para facilitar a adição de dois números de 4 bits usando um Arduino.”

### Demonstração
Demonstração ao vivo ou capturas de tela/vídeo mostrando o software em ação.

### Detalhes técnicos
Destaque os pinos de entrada e saída específicos usados ​​no Arduino.

---

## Visão geral dos recursos desenvolvidos

### Descrição do Software
Criamos um programa que utiliza um Arduino para somar dois números de 4 bits.

### Detalhes de configuração
- **Pinos de entrada:** Os pinos 0-7 e o pino 13 são usados ​​para ler os números e um sinal de controle.
- **Pinos de saída:** Os pinos 8 a 12 são usados ​​para exibir o resultado e o bit de transporte.

### Funcionalidades
O software inclui funções para adição bit a bit e cálculo de carry bit.

### Fluxo de trabalho
No loop principal, o programa lê continuamente as entradas e o sinal de controle. Quando o sinal de controle é ativado, ele realiza a adição e atualiza os pinos de saída com os resultados.

---

## Visão geral das atividades futuras

### Otimização
Os planos futuros envolvem a otimização do código para melhorar o desempenho.

### Operações Adicionais
Apresentando operações adicionais, como subtração e multiplicação.

### Teste
Realização de testes extensivos para garantir precisão e confiabilidade.

### Documentação
Desenvolvimento de documentação abrangente com instruções detalhadas de uso e manutenção.

### Teste automatizado
Implementação de testes automatizados para agilizar o processo de validação.

---

## Visão geral de bugs resolvidos e pendentes

### Problemas resolvidos
- Corrigidos problemas relacionados a leituras imprecisas dos pinos de entrada.
- Ajustou a lógica para cálculos de carry bit.

### Questões Pendentes
- Abordar comportamento inconsistente com certas entradas.
- Melhorar a estabilidade das leituras dos pinos em ambientes ruidosos.

### Plano de ação
- Identificar as causas raiz dos bugs restantes.
- Implementação de correções necessárias.
- Reavaliar após cada ajuste para garantir que os problemas sejam resolvidos.

---

## Descrição do Código

### Variáveis Globais

```cpp
int soma = 13; // Variável para armazenar o sinal de soma do pino 13
int carryBit = 0; // Variável para armazenar o bit de carry para adição

// Variáveis para armazenar os nibbles de entrada (valores de 4 bits)
int nib1a, nib1b, nib1c, nib1d = 0;
int nib2a, nib2b, nib2c, nib2d = 0;

// Variáveis para armazenar os nibbles de resultado
int res1a, res1b, res1c, res1d = 0;



markdown
Copiar código
# Projeto de Somador de 4 Bits com Arduino

## Índice

1. [Organização de Diretórios e Arquivos](#organização-de-diretórios-e-arquivos)
2. [Software Demonstration](#software-demonstration)
3. [Overview of Developed Features](#overview-of-developed-features)
4. [Overview of Future Activities](#overview-of-future-activities)
5. [Overview of Resolved and Pending Bugs](#overview-of-resolved-and-pending-bugs)
6. [Descrição do Código](#descrição-do-código)
7. [Como Usar](#como-usar)
8. [Licença](#licença)

---

## Organização de Diretórios e Arquivos

### Estrutura Comum

- **`docs/`**: Diretório principal para os arquivos de documentação.
  - **`index.md`**: Arquivo principal de entrada.
  - **`overview.md`**: Uma visão geral do projeto ou software.
  - **`installation.md`**: Instruções de instalação.
  - **`usage.md`**: Guia de uso do software.
- **`api/`**: Diretório para documentação da API, se aplicável.
  - **`index.md`**: Arquivo principal de documentação da API.
- **`examples/`**: Exemplos de código ou uso.
- **`images/`**: Imagens utilizadas na documentação.
- **`LICENSE`**: Arquivo de licença do software.
- **`CONTRIBUTING.md`**: Diretrizes para contribuições.
- **`README.md`**: Informações básicas sobre o projeto.

---

## Software Demonstration

### Introduction to the Software
"This software was developed to facilitate the addition of two 4-bit numbers using an Arduino."

### Demonstration
Live demonstration or screenshots/video showing the software in action.

### Technical Details
Highlight the specific input and output pins used on the Arduino.

---

## Overview of Developed Features

### Software Description
We have created a program that employs an Arduino to sum two 4-bit numbers.

### Configuration Details
- **Input Pins:** Pins 0-7 and pin 13 are used to read the numbers and a control signal.
- **Output Pins:** Pins 8-12 are used to display the result and the carry bit.

### Functionalities
The software includes functions for bit-wise addition and carry bit computation.

### Workflow
In the main loop, the program continuously reads the inputs and control signal. When the control signal is activated, it performs the addition and updates the output pins with the results.

---

## Overview of Future Activities

### Optimization
Future plans involve optimizing the code for enhanced performance.

### Additional Operations
Introducing additional operations such as subtraction and multiplication.

### Testing
Conducting extensive tests to ensure accuracy and reliability.

### Documentation
Developing comprehensive documentation with detailed usage and maintenance instructions.

### Automated Testing
Implementing automated tests to streamline the validation process.

---

## Overview of Resolved and Pending Bugs

### Resolved Issues
- Corrected problems related to inaccurate input pin readings.
- Adjusted the logic for carry bit calculations.

### Pending Issues
- Addressing inconsistent behavior with certain inputs.
- Improving the stability of pin readings in noisy environments.

### Action Plan
- Identifying root causes of the remaining bugs.
- Implementing necessary fixes.
- Reevaluating after each adjustment to ensure issues are resolved.

---

## Descrição do Código

### Variáveis Globais

```cpp
int soma = 13; // Variável para armazenar o sinal de soma do pino 13
int carryBit = 0; // Variável para armazenar o bit de carry para adição

// Variáveis para armazenar os nibbles de entrada (valores de 4 bits)
int nib1a, nib1b, nib1c, nib1d = 0;
int nib2a, nib2b, nib2c, nib2d = 0;

// Variáveis para armazenar os nibbles de resultado
int res1a, res1b, res1c, res1d = 0;
Função setup()
Configura os pinos de entrada e saída.

cpp
Copiar código
void setup() {
    // Configurar pinos 0 a 7 como entrada para leitura dos nibbles
    pinMode(0, INPUT);
    pinMode(1, INPUT);
    pinMode(2, INPUT);
    pinMode(3, INPUT);
    pinMode(4, INPUT);
    pinMode(5, INPUT);
    pinMode(6, INPUT);
    pinMode(7, INPUT);

    // Configurar pinos 8 a 12 como saída para o resultado
    pinMode(8, OUTPUT);
    pinMode(9, OUTPUT);
    pinMode(10, OUTPUT);
    pinMode(11, OUTPUT);
    pinMode(12, OUTPUT);

    // Configurar pino 13 como entrada para o sinal de soma
    pinMode(13, INPUT);
}
Função somaBit(int b1a, int b2a, int cBit)
Realiza a soma bit a bit sem carry utilizando a operação XOR.

cpp
Copiar código
int somaBit(int b1a, int b2a, int cBit) {
    return (b1a ^ b2a) ^ cBit;
}
Função somaCarryBit(int b1a, int b2a, int cBit)
Calcula o bit de carry para a soma bit a bit utilizando operações AND.

cpp
Copiar código
int somaCarryBit(int b1a, int b2a, int cBit) {
    return (b1a && b2a) || (b1a && cBit) || (b2a && cBit);
}
Função loop()
Executa continuamente para ler os nibbles de entrada, realizar a soma, e escrever o resultado nos pinos de saída.

cpp
Copiar código
void loop() {
    soma = digitalRead(13); // Ler o sinal de soma do pino 13

    // Ler os nibbles de entrada dos pinos 0 a 7
    nib1a = digitalRead(0);
    nib1b = digitalRead(1);
    nib1c = digitalRead(2);
    nib1d = digitalRead(3);
    nib2a = digitalRead(4);
    nib2b = digitalRead(5);
    nib2c = digitalRead(6);
    nib2d = digitalRead(7);

    if (soma == 1) { // Se o sinal de soma estiver ativo
        carryBit = 0; // Inicializar o bit de carry para 0

        // Realizar a soma bit a bit para cada bit dos nibbles
        res1a = somaBit(nib1a, nib2a, carryBit);
        carryBit = somaCarryBit(nib1a, nib2a, carryBit);
        res1b = somaBit(nib1b, nib2b, carryBit);
        carryBit = somaCarryBit(nib1b, nib2b, carryBit);
        res1c = somaBit(nib1c, nib2c, carryBit);
        carryBit = somaCarryBit(nib1c, nib2c, carryBit);
        res1d = somaBit(nib1d, nib2d, carryBit);
        carryBit = somaCarryBit(nib1d, nib2d, carryBit);
    }

    // Escrever os nibbles de resultado nos pinos de saída 8 a 12
    digitalWrite(8, res1a);
    digitalWrite(9, res1b);
    digitalWrite(10, res1c);
    digitalWrite(11, res1d);
    digitalWrite(12, carryBit); // Escrever o bit de carry final no pino 12
}
Como Usar
Conectar os pinos 0 a 7 do Arduino a um dispositivo que fornece os nibbles de entrada.
Conectar os pinos 8 a 12 do Arduino aos dispositivos onde os resultados devem ser exibidos.
Carregar o código no Arduino e alimentar o microcontrolador.
Quando o pino 13 estiver ativo, o Arduino realizará a soma dos nibbles de entrada e exibirá o resultado nos pinos de saída.
Licença
Este projeto está licenciado sob a MIT License.


