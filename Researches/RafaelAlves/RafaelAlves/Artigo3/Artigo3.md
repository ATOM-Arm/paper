# Braço Robótico Articulado Controlado Pelo Arduino

**Autor**: Agnaldo de Abreu Lima, Micki John de Oliveira, Ricardo Wolf, Leomar Besen

**Instituição**: Faculdade Anhanguera Jaraguá do Sul

---

## 1.Objetivo e Aplicação

O objetivo do trabalho foi desenvolver um protótipo de um braço robótico manipulador para demonstrar a aplicação da robótica em ambientes industriais, bem como desenvolver os algoritmos de controle para a plataforma Arduino. A aplicação prática do protótipo é a manipulação de objetos (carga e descarga), controlada manualmente por um operador.

---

## 2. Tecnologias Utilizadas

O protótipo foi construído com os seguintes componentes:

- **Estrutura**: Um kit de braço robótico fabricado em MDF
- **Microcontrolador**: Uma placa Arduino Mega 2560 para o controle central
- **Atuadores**: Quatro micro servo motores modelo SG90
- **Interface de Controle**: O braço é controlado por um joystick NUNCHUCK, que possui 2 eixos para controle de movimento e um acelerômetro de 3 eixos. Os movimentos do braço são proporcionais aos comandos do joystick
- **Software**: O código foi desenvolvido na IDE do Arduino (versão 1.8.5). A programação consiste em ler os valores analógicos dos eixos do joystick (variando de 0 a 1023) e mapeá-los para valores angulares para os servos (de 1 a 180 graus)

---

## 3. Desafios e Soluções Encontradas

Durante os testes, o projeto enfrentou vários problemas técnicos:

- **Falha de Comunicação**: Inicialmente, o braço não se movia devido a falhas na comunicação entre o software e o hardware. A solução envolveu um processo de depuração e testes para corrigir o código
- **Problemas Elétricos**: Foi identificado um diferencial de aterramento entre a fonte de alimentação dos servos e o circuito de controle, o que impedia o funcionamento correto. A solução foi corrigir a ligação elétrica
- **Qualidade dos Componentes**: Houve suspeita sobre a baixa qualidade dos servo motores, que pararam de funcionar ao usar uma fonte externa dedicada. Após correções, o protótipo voltou a operar normalmente
- **Movimentos Bruscos**: O principal desafio do resultado final foi a falta de suavidade nos movimentos do braço, que se mostraram bruscos. Os autores reconhecem que, para aplicações de alta precisão, seriam necessários novos estudos e um aperfeiçoamento do código para obter movimentos graduais e lineares

---

## 4. Conclusão e Contribuição para o Conhecimento

O trabalho conseguiu desenvolver um protótipo funcional de um braço manipulador, que cumpre o objetivo de simular sua aplicação em um cenário industrial de forma simplificada. A pesquisa evidenciou a complexidade envolvida na implantação da robótica, que exige uma conjuntura de infraestrutura, software maduro e mão de obra especializada. A principal contribuição foi promover um envolvimento prático entre as áreas de mecânica, eletrônica e automação, resultando em um modelo de estudos que pode ser utilizado para simulações e futuros aperfeiçoamentos.