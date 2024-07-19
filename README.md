
Software Demonstration
Introduction to the Software
"This software was developed to facilitate the addition of two 4-bit numbers using an Arduino."

Demonstration
Live demonstration or screenshots/video showing the software in action.

Technical Details
Highlight the specific input and output pins used on the Arduino.

Overview of Developed Features
Software Description
We have created a program that employs an Arduino to sum two 4-bit numbers.

Configuration Details
Input Pins: Pins 0-7 and pin 13 are used to read the numbers and a control signal.
Output Pins: Pins 8-12 are used to display the result and the carry bit.
Functionalities
The software includes functions for bit-wise addition and carry bit computation.

Workflow
In the main loop, the program continuously reads the inputs and control signal.
When the control signal is activated, it performs the addition and updates the output pins with the results.
Overview of Future Activities
Optimization
Future plans involve optimizing the code for enhanced performance.

Additional Operations
Introducing additional operations such as subtraction and multiplication.

Testing
Conducting extensive tests to ensure accuracy and reliability.

Documentation
Developing comprehensive documentation with detailed usage and maintenance instructions.

Automated Testing
Implementing automated tests to streamline the validation process.

Overview of Resolved and Pending Bugs
Resolved Issues
Corrected problems related to inaccurate input pin readings.
Adjusted the logic for carry bit calculations.
Pending Issues
Addressing inconsistent behavior with certain inputs.
Improving the stability of pin readings in noisy environments.
Action Plan
Identifying root causes of the remaining bugs.
Implementing necessary fixes.
Reevaluating after each adjustment to ensure issues are resolved.
Descrição do Código
Variáveis Globais
cpp
Copiar código
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
