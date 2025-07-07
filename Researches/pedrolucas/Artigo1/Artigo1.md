# Desenvolvimento de um Sistema de Visão para Detecção de Objetos Embarcado em um Braço Robótico

---

## 1. Introdução

A integração da visão computacional com braços robóticos tem impulsionado o desenvolvimento de sistemas autônomos mais precisos e inteligentes em contextos acadêmicos e industriais. O trabalho desenvolvido por Soares e Dias (UEFS) exemplifica esse avanço ao propor um sistema embarcado para detecção e mensuração de objetos utilizando o módulo ESP32-CAM e técnicas modernas de aprendizado profundo.

## 2. Tecnologias Utilizadas

O sistema de visão proposto combina sensores físicos e técnicas de inteligência artificial para possibilitar que um braço robótico reconheça, meça e manipule objetos. Os principais componentes e tecnologias são:

- **ESP32-CAM**: microcontrolador com sensor de imagem OV2640, utilizado para captura das imagens. É leve, compacto e de baixo custo, o que favorece sua integração direta ao braço robótico.
- **Sensor de Distância VL53L0X**: sensor a laser que mede a distância entre o braço e o objeto, essencial para a mensuração real das dimensões.
- **Modelo de Detecção EfficientDet-Lite0**: arquitetura baseada em EfficientNet combinada com BiFPN, treinada por transferência de aprendizado com o dataset COCO 2017. Exportado para o formato TensorFlow Lite.
- **Modelo de Mensuração por Regressão Linear**: relaciona pixels da imagem com as medidas reais do objeto, com base na distância informada pelo sensor.

Essas tecnologias permitem que o sistema detecte objetos (no caso, peças de Lego) e estime suas dimensões, viabilizando o planejamento de ações pelo braço robótico.

## 3. Desafios Enfrentados

Apesar dos avanços tecnológicos, diversos obstáculos surgiram durante o desenvolvimento:

- **Limitações de Hardware do ESP32-CAM**: embora o modelo EfficientDet-Lite0 seja compacto, ainda assim excedeu a capacidade de memória do ESP32-CAM. Isso forçou o redirecionamento do processamento para um computador externo, comprometendo a ideia de um sistema totalmente embarcado.
- **Restrições de Resolução e Aquecimento**: em altas resoluções (1600×1200), o microcontrolador não conseguia manter uma taxa de quadros adequada, além de apresentar superaquecimento.
- **Precisão na Perspectiva**: o sistema apresentou erros ao estimar medidas de objetos inclinados ou não alinhados paralelamente ao plano da câmera, revelando limitações na consideração de profundidade.
- **Desempenho do Sensor de Distância**: acima de 340 mm, o sensor apresentou erros significativos, afetando a acurácia da mensuração.

## 4. Resultados Obtidos

- O modelo de detecção obteve 81,92% de precisão média (AP) no conjunto de validação e 61,86% no teste, com melhor desempenho para objetos grandes.
- O modelo de mensuração alcançou RMSE inferior a 10 mm para distâncias de até 340 mm.
- O sistema mostrou ser funcional em cenários controlados, especialmente quando o objeto está bem posicionado (sem inclinação) e a uma distância adequada.

## 5. Conclusões e Trabalhos Futuros

A pesquisa demonstra a viabilidade de integrar visão computacional a braços robóticos usando recursos acessíveis. Apesar das limitações enfrentadas, a arquitetura proposta é eficaz para tarefas de detecção e mensuração em curto alcance. Como propostas futuras, os autores sugerem:

- Desenvolver modelos mais leves para possibilitar o embarque direto no ESP32-CAM.
- Utilizar sensores de distância mais robustos.
- Incorporar visão estéreo ou técnicas de reconstrução 3D para lidar melhor com objetos em perspectiva.

### Considerações Finais

O estudo reforça a importância da visão computacional na robótica moderna e expõe as complexidades técnicas envolvidas na sua aplicação prática. Ele também evidencia como a escolha de hardware e algoritmos deve ser cuidadosamente balanceada para garantir desempenho e viabilidade, especialmente em sistemas embarcados.
