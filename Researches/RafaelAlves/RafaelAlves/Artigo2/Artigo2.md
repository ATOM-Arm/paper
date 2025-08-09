# Braço Robótico: Aplicações Gerais e a Interação Homem-Máquina

**Autor**: Nathan Jeske Espindola

**Ano**: 2023

**Instituição**: Pontifícia Universidade Católica do Rio Grande do Sul (PUCRS) 

--- 

## 1.Objetivo e Aplicação

O principal objetivo deste trabalho é estudar e implementar um braço robótico de 5 graus de liberdade com foco na interação homem-máquina. A ideologia do projeto é explorar a viabilidade de usar robôs em áreas que exigem colaboração com humanos, como a saúde (auxílio em procedimentos) e a inclusão de profissionais com deficiência motora. A aplicação prática desenvolvida é um protótipo genérico que é controlado por gestos da mão, utilizando inteligência artificial para a interpretação dos movimentos

---

## 2. Tecnologias de Visão Computacional Aplicadas

 interação homem-máquina foi viabilizada por um sistema de visão computacional que não depende de sensores no braço, mas sim de uma câmera externa
 software:

 - **Software e Bibliotecas**: O reconhecimento de gestos foi desenvolvido em linguagem Python, utilizando a biblioteca OpenCV para processamento de imagem e a Mediapipe para detecção e rastreamento dos pontos da mão humana
 - **Funcionamento**: A aplicação captura o vídeo da mão do usuário, identifica os dedos que estão levantados ou abaixados e converte essa informação em um dado binário (ex: [1, 1, 0, 0, 0]). Esse dado é enviado via porta de comunicação serial para o microcontrolador que comanda o braço
 - **Controle**: O microcontrolador ESP32 TTGO recebe os dados binários e os converte em comandos de movimento para os servo-motores , onde cada dedo controla um eixo específico do braço
 - **Otimização**: Foi utilizado o sistema operacional de tempo real FreeRTOS, que permite a execução simultânea de tarefas, garantindo que os múltiplos servo-motores se movam de forma concorrente e fluida

 ---

 ## 3. Desafios e Soluções Encontradas 

 - **Desafio da Interação Segura**: O maior desafio discutido no trabalho não é técnico, mas conceitual: garantir que um robô possa interagir com humanos de forma segura, especialmente em aplicações críticas como na área da saúde, onde um erro pode causar danos graves. A solução adotada no escopo do projeto foi criar um protótipo de estudo genérico, sem aplicá-lo diretamente em um cenário real, destacando que a validação por profissionais da área seria indispensável
 - **Desafio do Movimento Simultâneo**: Fazer com que todos os 5 eixos do braço se movam de forma coordenada e simultânea é um desafio de programação. A solução foi implementar o FreeRTOS, que gerencia cada servo-motor como uma tarefa independente, permitindo o paralelismo e a fluidez dos movimentos

 ---

 ## 4. Conclusão e Contribuição para o Conhecimento

 O trabalho demonstra que a integração de bibliotecas de visão computacional como OpenCV e Mediapipe com microcontroladores modernos como o ESP32 é uma forma eficaz e de baixo custo para criar interfaces homem-máquina intuitivas, como o controle por gestos. A pesquisa conclui que, embora a tecnologia para automação colaborativa esteja acessível, o principal desafio para sua adoção em larga escala é garantir a segurança, a ética e a confiabilidade, o que exige protocolos rigorosos e colaboração interdisciplinar. O projeto serve como um ponto de partida para estudos mais aprofundados sobre robôs que cooperam com seres vivos em tarefas complexas

