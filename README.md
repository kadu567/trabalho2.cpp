Documentação do Projeto: Somador Completo com Arduino
1. Introdução
Este projeto tem como objetivo implementar um somador completo utilizando uma placa Arduino. O somador completo é um componente digital que calcula a soma de dois bits de entrada, levando em consideração um bit de carry de entrada.

2. Componentes Necessários
1 Placa Arduino (Uno, Mega, etc.)
8 Resistores de 220Ω (opcional, dependendo do tipo de entrada)
8 Botões (para entradas digitais)
5 LEDs (para saídas digitais)
1 Protoboard
Fios de Conexão

3. Descrição do Projeto
O projeto consiste em ler dois nibbles (4 bits cada) de entrada através de botões conectados aos pinos digitais do Arduino. Esses nibbles representam os dois números a serem somados. O somador completo calcula a soma desses dois números bit a bit, considerando o carry bit gerado em cada operação. O resultado da soma e o carry final são exibidos em LEDs conectados aos pinos de saída do Arduino.

4. Diagrama de Conexões
Pinos de Entrada:
- Pino 0: Bit 1 do primeiro número (nib1a)
- Pino 1: Bit 2 do primeiro número (nib1b)
- Pino 2: Bit 3 do primeiro número (nib1c)
- Pino 3: Bit 4 do primeiro número (nib1d)
- Pino 4: Bit 1 do segundo número (nib2a)
- Pino 5: Bit 2 do segundo número (nib2b)
- Pino 6: Bit 3 do segundo número (nib2c)
- Pino 7: Bit 4 do segundo número (nib2d)
- Pino 13: Sinal de soma (soma)

Pinos de Saída:
- Pino 8: Bit 1 do resultado (res1a)
- Pino 9: Bit 2 do resultado (res1b)
- Pino 10: Bit 3 do resultado (res1c)
- Pino 11: Bit 4 do resultado (res1d)
- Pino 12: Carry final (carryBit)

5. Código Fonte
// TÉCNICO EM DESENVOLVIMENTO DE SISTEMAS - SENAC NH
// Programa base para TRABALHO 2
// PROF.: Glauber Kiss de Souza
// DISC.: Analisar Orient. Técnicas
// Licença MIT
// Copyright (c) 2024 
// É concedida permissão, gratuitamente, a qualquer pessoa que obtenha uma cópia
// deste software e dos arquivos de documentação associados (o "Software"), para lidar
// no Software sem restrição, incluindo, sem limitação, os direitos de usar, copiar, modificar, mesclar, publicar, distribuir, sublicenciar e/ou vender
// cópias do Software, e permitir às pessoas a quem o Software é
// fornecido para o efeito, nas seguintes condições:
// O aviso de copyright acima e este aviso de permissão devem ser incluídos em todos
// cópias ou partes substanciais do Software.
// O SOFTWARE É FORNECIDO "COMO ESTÁ", SEM GARANTIA DE QUALQUER TIPO, EXPRESSA OU
// IMPLÍCITA, INCLUINDO MAS NÃO SE LIMITANDO ÀS GARANTIAS DE COMERCIALIZAÇÃO,
// ADEQUAÇÃO A UM DETERMINADO FIM E NÃO VIOLAÇÃO. EM NENHUM CASO OS AUTORES OU
// OS DETENTORES DO DIREITO AUTORAL SERÃO RESPONSÁVEIS POR QUALQUER RECLAMAÇÃO, DANOS OU OUTRAS
// RESPONSABILIDADE, SEJA EM UMA AÇÃO DE CONTRATO, TORT OU DE OUTRA FORMA, DECORRENTE DE,
// FORA OU EM CONEXÃO COM O SOFTWARE OU O USO OU OUTRAS NEGOCIAÇÕES NO
// SOFTWARE.

int soma = 13; // Variable to store the sum signal from pin 13
int carryBit = 0; // Variable to store the carry bit for addition

// Variables to store the input nibbles (4-bit values)
int nib1a, nib1b, nib1c, nib1d = 0;
int nib2a, nib2b, nib2c, nib2d = 0;

// Variables to store the result nibbles
int res1a, res1b, res1c, res1d = 0;

void setup()
{
    // Configure pins 0 to 7 as input for reading nibbles
    pinMode(0, INPUT);
    pinMode(1, INPUT);
    pinMode(2, INPUT);
    pinMode(3, INPUT);
    pinMode(4, INPUT);
    pinMode(5, INPUT);
    pinMode(6, INPUT);
    pinMode(7, INPUT);
    
    // Configure pins 8 to 12 as output for the result
    pinMode(8, OUTPUT);
    pinMode(9, OUTPUT);
    pinMode(10, OUTPUT);
    pinMode(11, OUTPUT);
    pinMode(12, OUTPUT);
    
    // Configure pin 13 as input for the sum signal
    pinMode(13, INPUT);
}

// Function to perform bit-wise addition without carry
int somaBit(int b1a, int b2a, int cBit)
{
    int bitResult = 0;
    if ((b1a ^ b2a) ^ cBit) // XOR operation for bit addition
    {
        bitResult = 1;
    }
    else
    {
        bitResult = 0;
    }
    return bitResult;
}

// Function to calculate the carry bit for bit-wise addition
int somaCarryBit(int b1a, int b2a, int cBit)
{
    // Carry is produced if two or more of the inputs are 1
    if ((b1a && b2a) || (b1a && cBit) || (b2a && cBit)) // AND operation for carry calculation
    {
        cBit = 1;
    }
    else
    {
        cBit = 0;
    }
    return cBit;
}

void loop()
{
    soma = digitalRead(13); // Read the sum signal from pin 13

    // Read the input nibbles from pins 0 to 7
    nib1a = digitalRead(0);
    nib1b = digitalRead(1);
    nib1c = digitalRead(2);
    nib1d = digitalRead(3);
    nib2a = digitalRead(4);
    nib2b = digitalRead(5);
    nib2c = digitalRead(6);
    nib2d = digitalRead(7);
    
    if (soma == 1) // If sum signal is active
    {
        carryBit = 0; // Initialize carry bit to 0

        // Perform bit-wise addition for each bit in the nibbles
        res1a = somaBit(nib1a, nib2a, carryBit);
        carryBit = somaCarryBit(nib1a, nib2a, carryBit);
        res1b = somaBit(nib1b, nib2b, carryBit);
        carryBit = somaCarryBit(nib1b, nib2b, carryBit);
        res1c = somaBit(nib1c, nib2c, carryBit);
        carryBit = somaCarryBit(nib1c, nib2c, carryBit);
        res1d = somaBit(nib1d, nib2d, carryBit);
        carryBit = somaCarryBit(nib1d, nib2d, carryBit);
    }
    
    // Write the result nibbles to output pins 8 to 12
    digitalWrite(8, res1a);
    digitalWrite(9, res1b);
    digitalWrite(10, res1c);
    digitalWrite(11, res1d);
    digitalWrite(12, carryBit); // Write the final carry bit to pin 12
}

6. Funcionamento
Configuração Inicial: No setup(), os pinos de entrada (0 a 7 e 13) são configurados como INPUT e os pinos de saída (8 a 12) como OUTPUT.
Leitura de Dados: No loop(), os valores dos nibbles de entrada e o sinal de soma são lidos dos pinos configurados.
Cálculo da Soma: Se o sinal de soma estiver ativo (igual a 1), a função somaBit é chamada para cada bit dos nibbles, e a função somaCarryBit calcula o carry bit.
Escrita dos Resultados: Os resultados da soma e o carry final são escritos nos pinos de saída.

7. Conclusão
Este projeto demonstra a implementação de um somador completo em um sistema Arduino, utilizando componentes básicos como botões e LEDs. A lógica de soma bit a bit com carry é fundamental em circuitos digitais e serve como base para o entendimento de operações aritméticas mais complexas em eletrônica digital.
