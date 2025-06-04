# 🌊 Projeto de Monitoramento de Enchentes com Sensor Ultrassônico

---

## 📌 Descrição do Problema

Enchentes são desastres naturais recorrentes no Brasil, especialmente em regiões próximas a rios e áreas urbanas mal planejadas. Muitas vezes, moradores dessas regiões não recebem alertas a tempo para proteger seus bens ou evacuar em segurança. A falta de monitoramento acessível e de respostas rápidas pode gerar perdas humanas, materiais e ambientais significativas.

---

## 💡 Visão Geral da Solução

Desenvolvemos um sistema simples e funcional que **monitora o nível da água em tempo real** e **emite alertas visuais e sonoros** de acordo com o risco de enchente. A ideia é que ele seja instalado próximo ao leito de um rio e funcione de forma autônoma, avisando a população local sobre possíveis riscos iminentes, mesmo sem acesso à internet ou aplicativos.

### 🔧 Componentes usados:
- Sensor Ultrassônico (HC-SR04)
- LEDs (Verde, Amarelo e Vermelho)
- Buzzer
- Arduino Uno

---

### 🖼️ Ilustração do Funcionamento

```
          SENSOR ULTRASSÔNICO
                ↓↓↓
     (mede a distância até o nível da água)

        ↓ DISTÂNCIA INTERPRETADA ↓

🟢 > 1 metros  → LED VERDE (Nível normal)  
🟡 ≤ 1 metro   → LED AMARELO + Som agudo (Atenção)  
🔴 ≤ 0.5 metro → LED VERMELHO + Som grave (Alerta Máximo)
```

---

## ▶️ Como Simular o Projeto

### 🔗 Link direto para o projeto no simulador Wokwi:
👉 [Acessar Projeto no Wokwi](https://wokwi.com/projects/432229165635617793)

### 🧪 Passos para simular:
1. Acesse o link do projeto acima;
2. Clique em **"Start Simulation"**;
3. No painel do sensor, altere manualmente a distância (ex: 200cm, 100cm, 50cm);
4. Observe a resposta do sistema:
   - LED verde acende em distância segura;
   - LED amarelo e som agudo com nível intermediário;
   - LED vermelho e som grave em situação de risco.

---

## 🎥 Vídeo Demonstrativo

📺 Assista à explicação e demonstração completa do projeto:  
🔗 [Clique aqui para assistir no YouTube](https://youtu.be/4BAEEN4dSP4)

---

## 🧠 Código-Fonte

```cpp
#define trigPin 9
#define echoPin 8
#define buzzer 10
#define ledVerde 2
#define ledAmarelo 3
#define ledVermelho 4

long duration;
float distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(ledVerde, OUTPUT);
  pinMode(ledAmarelo, OUTPUT);
  pinMode(ledVermelho, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // Envia pulso ultrassônico
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Calcula distância
  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  Serial.print("Distância: ");
  Serial.print(distance);
  Serial.println(" cm");

... (40 linhas)
