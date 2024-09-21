# Projeto: Relógio com RTC DS1302 e Display LCD I2C

Este projeto utiliza um **Arduino Uno**, um **módulo RTC DS1302**, e um **display LCD I2C** para exibir a data e a hora no formato de 24 horas (horário militar).

## Descrição

O código deste projeto configura o RTC DS1302 para fornecer a data e hora atuais. Esses dados são exibidos em um display LCD de 16x2 com interface I2C. O RTC DS1302 é um relógio de tempo real que mantém a data e a hora mesmo quando o Arduino está desligado, graças a uma bateria de backup. A exibição da hora é feita no formato de 24 horas (HH:MM:SS), e a data é mostrada no formato `DD/MM/AA`.

## Componentes Necessários

- 1 x Arduino Uno
- 1 x Módulo RTC DS1302
- 1 x Display LCD 16x2 com interface I2C
- Fios de conexão
- Protoboard (opcional)
- Bateria para o RTC (opcional, mas recomendada para manter o horário correto)

## Esquema de Conexão

### Conexão do **RTC DS1302**:
- **VCC** → 5V do Arduino
- **GND** → GND do Arduino
- **CLK** → Pino digital 6 do Arduino
- **DAT** → Pino digital 7 do Arduino
- **RST** → Pino digital 8 do Arduino

### Conexão do **Display LCD I2C**:
- **VCC** → 5V do Arduino
- **GND** → GND do Arduino
- **SDA** → Pino A4 do Arduino
- **SCL** → Pino A5 do Arduino

## Bibliotecas Utilizadas

- **Wire.h**: Necessária para a comunicação I2C entre o Arduino e o display LCD. Essa biblioteca já está incluída no Arduino IDE.
- **LiquidCrystal_I2C.h**: Biblioteca para controlar displays LCD via interface I2C. Pode ser instalada diretamente na IDE do Arduino.
- **ThreeWire.h** e **RtcDS1302.h**: Bibliotecas para controlar o módulo RTC DS1302. Podem ser baixadas [aqui](https://www.github.com/Makuna/Rtc).

### Instalação das Bibliotecas

1. Abra a **Arduino IDE**.
2. Vá em **Sketch** → **Incluir Biblioteca** → **Gerenciar Bibliotecas**.
3. Procure por **LiquidCrystal I2C** e instale a biblioteca correspondente.
4. Para instalar as bibliotecas do RTC DS1302:
   - Faça o download da biblioteca **RtcDS1302** do repositório [Makuna/Rtc](https://github.com/Makuna/Rtc).
   - Após baixar, vá em **Sketch** → **Incluir Biblioteca** → **Adicionar .ZIP Library...** e selecione o arquivo baixado.

## Explicação do Código

O código está dividido em algumas seções principais:

1. **Importação de bibliotecas**: Carregamos as bibliotecas necessárias para a comunicação I2C, o display LCD e o RTC DS1302.
   
2. **Definição de pinos e objetos**: Definimos os pinos de conexão do RTC DS1302 e criamos os objetos responsáveis por controlar o RTC e o display LCD.

3. **Configuração (`setup`)**:
   - Inicializamos o display LCD com a função `lcd.begin()` e ligamos a luz de fundo.
   - Inicializamos o RTC com a função `rtc.Begin()`.
   - Verificamos se o RTC está funcionando corretamente. Se não estiver, ajustamos a data e hora manualmente (essa parte pode ser ajustada conforme necessário).

4. **Loop principal (`loop`)**:
   - A cada segundo, o Arduino pega a data e hora atual do RTC com a função `rtc.GetDateTime()` e formata a exibição no display LCD.
   - A data é exibida no formato `DD/MM/YY`.
   - A hora é exibida no formato de 24 horas (militar) `HH:MM:SS`.

```cpp
lcd.print(now.Day() < 10 ? "0" : ""); // Exibe zero à esquerda se o dia for menor que 10
lcd.print(now.Hour() < 10 ? "0" : ""); // Exibe zero à esquerda se a hora for menor que 10
