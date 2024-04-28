# conexão-de-botão-com-arduino

>[!NOTE]
>Todo esse projeto está disponível do meu perfil no [Tinkercard](https://www.tinkercad.com/things/6fse1YqCfUX-conexao-de-botao-com-arduino?sharecode=VZ4HpY8nBWVcITHgirfD9bUPYlkDqwm3bEylo125AKw)

Projeto desenvolvido como atividade academica.

## Hardware 

- Botão
- Placa de ensaio Pequena
- Arduino Uno R3

![image](https://github.com/r2WillDev/conexao-de-botao-com-arduino/assets/106842143/5e3346bb-c5f6-4b8e-af44-0a0c6a541c6e)

## Código

1. Define o pino número 2 como buttonPin, que será usado para ler o estado de um botão.
2. Define o pino número 13 como ledPin, que será usado para controlar um LED.
3. Inicializa a variável botaoStatus com o valor 1. Esta variável armazenará o estado do botão.
4. Na função setup():
   - Configura o ledPin como uma saída usando a função pinMode(). Isso é necessário para controlar o LED.
   - Configura o buttonPin como uma entrada usando a função pinMode(). Isso é necessário para ler o estado do botão.
   - Ativa o resistor de pull-up interno para o buttonPin com a função digitalWrite(), definindo-o como HIGH. Isso é feito para garantir que o pino leia HIGH quando o botão não estiver pressionado.
5. Na função loop() que é executada repetidamente:
   - Lê o estado atual do botão com a função digitalRead() e armazena em botaoStatus.
   - Se botaoStatus for LOW (indicando que o botão está pressionado):
     - Liga o LED enviando um sinal HIGH para o ledPin com a função digitalWrite().
   - Se botaoStatus for HIGH (indicando que o botão não está pressionado):
     - Desliga o LED enviando um sinal LOW para o ledPin.
   - Introduz um pequeno atraso de 20 milissegundos com a função delay() para estabilizar a leitura do botão e evitar leituras falsas devido à trepidação.

Resumindo, quando o botão é pressionado, o LED da placa Arduino acende. Quando o botão é solto, o LED apaga. A função delay(20); ajuda a evitar leituras falsas devido à “trepidação” do botão (mudanças rápidas e breves no estado do botão).



```C++
// C++ code
//

int buttonPin = 2;
int ledPin = 13;
int botaoStatus = 1;
void setup()
{
  pinMode(ledPin, OUTPUT);
  pinMode(buttonPin, INPUT);
  digitalWrite(buttonPin, HIGH);
}

void loop()
{
  botaoStatus = digitalRead(buttonPin);
  if(LOW  == botaoStatus)
  {
  	digitalWrite(ledPin, HIGH);
  }
  else{
    digitalWrite(ledPin, LOW);
  }
	delay(20);
}

```

