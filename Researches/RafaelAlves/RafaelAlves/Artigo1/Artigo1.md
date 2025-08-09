# Linha de Produção Seletora com Braço Robótico de 5 Eixos

**Autores**: Ana Luiza Di Giovani, Anna Julya de Souza Gabelhere, Bryan Cezar dos Santos, Helena Rita Candido, Kaua Martins de Jesus, Raphael Periotto de Oliveira

**Ano**: 2024

**Instituição**: ETEC Paulino Botelho

---

## 1.Objetivo e Aplicação

O projeto tem como objetivo principal montar e programar uma linha de produção seletora para fins didáticos, demonstrando a realidade industrial de forma simplificada para os alunos da Etec Paulino Botelho. A aplicação consiste em uma esteira que transporta um objeto até um braço robótico de 5 eixos. O braço, por sua vez, utiliza sensores para identificar a cor do objeto e separá-lo em um recipiente correspondente, simulando um processo de automação industrial.

---

## 2. Tecnologias Utilizadas

O sistema foi desenvolvido integrando os seguintes componentes:

- **Microcontrolador**: A lógica de controle de todo o sistema é centralizada em uma placa Arduino Mega 2560
- **Braço Robótico**: Utiliza uma estrutura de alumínio com 5 eixos de liberdade , movido por múltiplos servo motores para garantir a precisão dos movimentos. A garra foi projetada e impressa em 3D com material ABS.
- **Esteira Transportadora**: Composta por uma estrutura de metal, roletes, uma manta emborrachada para o transporte dos objetos e um motor Bosch 12V para o acionamento.
- **Sensores (Visão e Detecção)**:

    - **Sensor de Cor**: Um sensor RGB TCS34725 é usado para identificar as cores dos objetos na esteira.

    - **Sensor de Distância**: Um sensor a laser VL53L1X detecta a presença e a posição do objeto ao final do percurso da esteira, acionando a parada do motor e a ação do braço
- **Componentes Adicionais**: Um multiplexador I2C (PCA9548A) foi utilizado para permitir a comunicação do Arduino com múltiplos sensores que compartilham o mesmo endereço. O circuito final foi soldado em uma placa de fenolite para maior robustez

---

## 3. Desafios e Soluções

O desenvolvimento do projeto enfrentou desafios práticos de montagem e integração:

- **Falta de Componentes**: A estrutura do braço robótico adquirida não possuía uma garra. A solução foi projetar uma garra customizada no software Autodesk Inventor e fabricá-la em uma impressora 3D. De forma similar, um acoplador para o motor da esteira também precisou ser desenhado e impresso em 3D
- **Ajustes Mecânicos**: A esteira, sendo uma doação, exigiu a regulagem e o tensionamento da manta emborrachada para garantir o deslizamento adequado dos objetos

---

## 4. Conclusão e Contribuição para o Conhecimento

O trabalho conclui que é viável construir um protótipo funcional de uma linha de produção automatizada utilizando componentes acessíveis. O sistema integrado demonstrou ser capaz de executar a tarefa de separação de objetos por cor de forma coordenada e eficiente, validando os conceitos teóricos de mecatrônica. A pesquisa contribui ao fornecer uma base sólida para projetos futuros e, principalmente, ao criar uma plataforma didática que pode ser utilizada para ensinar automação industrial de maneira prática, aumentando a qualidade do ensino e preparando melhor os alunos para o mercado de trabalho
