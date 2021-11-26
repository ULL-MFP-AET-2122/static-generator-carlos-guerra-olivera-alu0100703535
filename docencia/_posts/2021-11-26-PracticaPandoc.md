---
title: "Proyecto Full Store"
---
###### En este trabajo pretendemos generar un codigo que automatice el aforo de una tienda.

Para ello utilizaremos el [gitbloq](https://bitbloq.cc/) donde podremos programar por bloques, haciendo la practica dinámica y accesible para el alumnado.


El proceso se consiste en que al pasar por la puerta nuestro sensor detecta la entrada o salida de un usuario y suma o resta hasta llegar a 10 que es el aforo permitido, momento en el cual activara un led en rojo indicando que estamoa a full de capacidad.
A continuación, mostramos el código generado, que corresponde a nuestra programación por bloques.

~~~
uint8_t boton = 6;
uint8_t LedFull = 8;
uint8_t LedStatus = 10;
uint8_t SensorOUT = 3;
uint8_t SensorIN = 13;
float Switch = 0;
float Count = 0;
float Start = 0;
/***   Setup  ***/
void setup() {
    pinMode(boton, INPUT);
    pinMode(LedFull, OUTPUT);
    pinMode(LedStatus, OUTPUT);
    pinMode(SensorOUT, INPUT);
    pinMode(SensorIN, INPUT);
}
/***   Loop  ***/
void loop() {
    Switch = digitalRead(boton);
    if (Switch == 1) {
        digitalWrite(LedStatus, HIGH);
        Start = Switch + 1;
        while (Start == 1) {
            auto InfraIN = digitalRead(SensorIN);
            auto InfraOUT = digitalRead(SensorOUT);
            if (InfraIN == 1) {
                Count = InfraIN + 1;
            }
            if (InfraOUT == 1) {
                Count = InfraOUT - 1;
            }
            while (Count >= 10) {
                digitalWrite(LedFull, HIGH);
                delay(1000);
                digitalWrite(LedFull, LOW);
                delay(1000);
            }
            if (digitalRead(boton) == 1) {
                Start = 0;
                Switch = 0;
                digitalWrite(LedStatus, LOW);
            }
            else {
                Start = 1;
                Switch = 1;
            }
        }
    }
}
~~~