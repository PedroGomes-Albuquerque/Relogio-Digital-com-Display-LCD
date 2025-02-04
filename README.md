# Relógio com Arduino, DS1302 e Display LCD I2C

## Descrição

Este projeto utiliza um **Arduino Uno**, um **módulo RTC DS1302** e um **display LCD com interface I2C** para exibir a data e a hora em tempo real. O código inicializa o RTC, verifica sua validade e exibe as informações no LCD.

## Componentes Necessários

- Arduino Uno
- Módulo RTC DS1302
- Display LCD 16x2 com interface I2C
- Jumpers para conexão

## Conexões
![Rtc ](https://github.com/user-attachments/assets/5d02fa24-f2a4-45b0-9a44-20ef3e4aae2a)

### LCD I2C:

| Pino LCD | Pino Arduino |
| -------- | ------------ |
| VCC      | 5V           |
| GND      | GND          |
| SDA      | A4           |
| SCL      | A5           |

### RTC DS1302:

| Pino RTC | Pino Arduino |
| -------- | ------------ |
| VCC      | 5V           |
| GND      | GND          |
| CLK      | 6            |
| DAT      | 7            |
| RST      | 8            |

## Instalação de Bibliotecas

Antes de compilar e carregar o código no Arduino, instale as bibliotecas necessárias na IDE do Arduino:

- **Wire.h** (já incluída na IDE do Arduino)
- [**LiquidCrystal\_I2C.h**](https://github.com/fdebrabander/Arduino-LiquidCrystal-I2C-library) (para o LCD I2C)
- [**ThreeWire.h**](https://github.com/Makuna/Rtc/blob/master/src/ThreeWire.h) (para comunicação com o RTC DS1302)
- [**RtcDS1302.h**](https://github.com/Makuna/Rtc/blob/master/src/RtcDS1302.h) (para controle do RTC)

Você pode instalar as bibliotecas pela "Biblioteca Gerenciador" na IDE do Arduino.

## Funcionamento

1. O LCD exibe "Initializing..." ao ligar o sistema.
2. O RTC DS1302 é inicializado e sua data/hora são verificadas.
3. Caso o RTC não tenha uma data/hora válida, ele é configurado manualmente para `07/09/2024 00:00:00`.
4. O LCD exibe a data e a hora em tempo real, atualizando a cada segundo.
5. As informações também são enviadas para o monitor serial.

## Exemplo de Saída no LCD

```
07/09/24
12:30:45
```

## Exemplo de Saída no Monitor Serial

```
Date: 07/09/24
Time: 12:30:45
```


---

