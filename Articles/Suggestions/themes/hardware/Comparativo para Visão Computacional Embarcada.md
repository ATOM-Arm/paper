# Comparativo para Visão Computacional Embarcada em Robôs Educacionais

Comparativo entre ESP32-S3, Raspberry Pi Zero 2 W e ESP32-CAM, visando escolher as melhores opções para aplicações de visão computacional embarcada no projeto ATOM.

🧩 Tópicos ajustados:

## 1. Introdução aos Componentes Selecionados

* **ESP32-S3 (Xtensa LX7 + acel. vetorial):**
  Voltado para IA embarcada e visão computacional leve, com suporte a instruções SIMD e TensorFlow Lite Micro. Conectividade Wi-Fi/Bluetooth e suporte nativo a câmeras.

* **Raspberry Pi Zero 2 W (ARM Cortex-A53):**
  Capaz de rodar Linux, ideal para processar modelos de visão computacional mais robustos (OpenCV, YOLOv5, etc). Tem conectividade completa e GPIOs diversos.

* **ESP32-CAM (Xtensa LX6):**
  Solução ultra barata e compacta, ideal para streaming de vídeo e aplicações muito leves de detecção com IA.

---

## 2. Comparativo de Capacidades

| Plataforma            | Arquitetura    | Clock      | RAM              | Núcleos | Câmera nativa  | IA embarcada       | Conectividade  | Sistema Operacional     |
| --------------------- | -------------- | ---------- | ---------------- | ------- | -------------- | ------------------ | -------------- | ----------------------- |
| ESP32-CAM             | Xtensa LX6     | 240 MHz    | \~520 KB         | 2       | Sim (OV2640)   | Sim (leve)         | Wi-Fi          | Bare-metal / RTOS       |
| ESP32-S3              | Xtensa LX7     | 240 MHz    | \~512 KB + PSRAM | 2       | Sim (via DVP)  | Sim (TFLite Micro) | Wi-Fi, BLE     | Bare-metal / RTOS       |
| Raspberry Pi Zero 2 W | ARM Cortex-A53 | 1.0 GHz x4 | 512 MB           | 4       | Sim (CSI, USB) | Sim (full OpenCV)  | Wi-Fi, BT, USB | Linux (Raspbian/Debian) |

---

## 3. Aplicabilidades na Robótica Educacional

* **ESP32-CAM:**
  Ideal para projetos de transmissão de vídeo, detecção de movimento, QR codes ou faces, com custo extremamente baixo.

* **ESP32-S3:**
  Adequado para tarefas de visão computacional distribuída com processamento local de pequenas CNNs. Possui suporte oficial a TensorFlow Lite Micro e câmeras de alta resolução (como OV5640).

* **Raspberry Pi Zero 2 W:**
  Para cargas mais pesadas, como detecção de objetos (YOLO), segmentação, reconhecimento de gestos, com a vantagem de poder executar interfaces gráficas, Python completo e multitarefa real.

---

## 4. Preços e Acessibilidade no Brasil (2025)

| Plataforma            | Preço Aproximado  | Facilidade de Aquisição                |
| --------------------- | ----------------- | -------------------------------------- |
| ESP32-CAM             | R\$ 35 – R\$ 50   | Alta                                   |
| ESP32-S3 (DevKit)     | R\$ 60 – R\$ 90   | Alta                                   |
| Raspberry Pi Zero 2 W | R\$ 250 – R\$ 350 | Baixa (importação ou estoque limitado) |

---

## 5. Estudo de Caso: ATOM Project

No ATOM Project, propõe-se:

* **ESP32-S3** como controlador principal embarcado, executando tarefas de controle motor e visão computacional leve (ex: detecção de cores ou formas).
* **ESP32-CAM** como módulo de transmissão de vídeo em tempo real para monitoramento.
* **Raspberry Pi Zero 2 W** como unidade de processamento para visão embarcada mais pesada, conectada via rede local (Wi-Fi ou UART) ao ESP32-S3 para comandos inteligentes.

---

## 6. Conclusão

Utilizar as 3 plataformas de forma complementar pode criar um ecossistema distribuído, eficiente e de baixo custo para robôs educacionais. Essa abordagem permite dividir inteligentemente as tarefas entre os dispositivos:

* Baixo custo + boa potência com ESP32-S3
* Suporte a vídeo e transmissão com ESP32-CAM
* Visão computacional robusta com Raspberry Pi Zero 2 W

Essa arquitetura híbrida é mais poderosa e flexível que depender de apenas um microcontrolador tradicional.
