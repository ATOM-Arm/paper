# Matriz de Experimentos — Braço Robótico Controlado por Visão (ATOM)

**Objetivo:** matriz padronizada para garantir testes justos e auditáveis entre linguagens e plataformas, alinhada ao fluxo real do sistema: *Percepção → Planejamento/Controle → Operação Conjunta*.

**Instruções gerais:**
- Repetições: **≥10 execuções** por condição. Reportar média, desvio padrão, mínimo, máximo.
- Hardware compartilhado: usar mesma câmera, mesmo servo (MG996R) e mesma fonte de alimentação quando o teste comparar linguagens na mesma classe de hardware.
- Registrar: data/hora, versão do código, versões de bibliotecas, temperatura ambiente, fotos do setup, logs brutos.

---

## Tabela de Experimentos

| ID | Experimento | Etapa | Hardware | Linguagens/Implementações | Métricas Principais | Variáveis Controladas | Observações de Setup |
|----|-------------|-------|----------|---------------------------|----------------------|-----------------------|----------------------|
| P1 | Detecção estática de marcador (latência por frame) | Percepção | Raspberry Pi / PC | Python, C++, Rust, Java | Latência por frame (ms); FPS; erro de coordenada (px/mm) | Mesma imagem/cena; resolução; algoritmo (ArUco/Haar/Hue) | Captura direta na plataforma quando aplicável; para C++/Java/Rust, também rodar sobre imagens pré-gravadas para parity. |
| P2 | Robustez de detecção sob variação de iluminação | Percepção | Raspberry Pi / PC | Python, C++, Rust, Java | Queda de FPS (%), recall/precision, erro de coordenada | Iluminação alta/média/baixa; mesmo alvo | Controlar posição do alvo e medir luminância (lux). |
| P3 | Throughput de processamento por frame (single-frame alg.) | Percepção | Raspberry Pi / PC | Python (pipeline completo), C++, Rust, Java (processam imagens pré-gravadas) | Tempo por imagem (ms); uso de CPU (%); memória (MB) | Resoluções: 320×240, 640×480, 1280×720; build release | Rodar em CPU isolada (sem outras tarefas). |
| C1 | Latência comando→início de movimento (controle) | Controle | Arduino Uno, ESP32, Raspberry Pi (GPIO/PWM) | C++ (Arduino/ESP), Rust (ESP/RPi), Python (RPi), Java (RPi) | Latência (ms) entre envio do comando e movimento detectado; jitter | Mesmo servo, mesma fonte, mesmo método de envio (serial/I2C/GPIO) | Sensor físico (limit switch/IR) detecta início; medir com timestamping. |
| C2 | Precisão de posicionamento (erro final) | Controle | Arduino/ESP32/RPi | C++, Rust, Python, Java | Erro médio (° e mm); repetibilidade; desvio padrão | Mesmo braço e cinemática, mesma carga | Transformar coordenada em ângulo com função idêntica; medir posição com régua/calibrador ou câmera de verificação. |
| C3 | Ciclo completo 0°→180°→0° (tempo e corrente) | Controle | Arduino/ESP32/RPi | C++, Rust, Python, Java | Tempo ciclo (ms); consumo de corrente pico/medio (A) | Tensão fixa, mesma carga, mesma sequência de comandos | Usar medidor de corrente (shunt + ADC) e registrar perfil temporal. |
| OC1 | End-to-end: frame com alvo → braço inicia movimento | Operação Conjunta | (Visão:Raspberry Pi/PC) + (Controle:Arduino/ESP32/RPi) | Combinações: visão em Python + controle em C++; visão+controle na mesma linguagem | Latência E2E (ms); jitter; taxa de perda de frames | Mesmo algoritmo de detecção; mesma rota de comunicação (Serial/UDP) | Sincronizar logs de visão e controle (timestamps NTP/local). |
| OC2 | Rastreamento de alvo móvel (seguimento) | Operação Conjunta | Mesmo conjunto | Varia por implementação | Atraso médio no seguimento (ms); erro posicional dinâmico; estabilidade (overshoot) | Velocidade do alvo (mm/s); padrão de movimento (linear/circular) | Usar plataforma motorizada para mover alvo com velocidade controlada. |
| OC3 | Estresse computacional (visão pesada + controle) | Operação Conjunta | Raspberry Pi / SBC | Python (pipeline+NN), C++, Rust, Java | Degradação de latência (%); perda de frames; erro final | Carregar CPU com inferência NN ou tarefa extra | Medir quando QoS do controle degrada além de X ms ou Y mm. |
| S1 | Tempo de desenvolvimento & complexidade | Integração | — | Todas as linguagens | Horas-homem (h); linhas de código (LOC); bibliotecas necessárias; dificuldade (1-5) | Mesma tarefa descrita (ex.: pipeline simples + controle básico) | Fazer tarefa padronizada e cronometrar implementação. |
| S2 | Suporte a bibliotecas e limitações de hardware | Integração | Arduino, ESP32, RPi | Todas as linguagens | Lista de bibliotecas funcionais; limitações encontradas; problemas de compatibilidade | Mesma funcionalidade requerida (e.g., PWM, OpenCV, serial) | Registrar issues e contornar com notas. |

---

## Protocolos e Campos de Log (para cada execução)
- **Identificador do experimento (ID)**
- **Data/Hora (ISO)**
- **Hardware (modelo, serial)**
- **Versão do firmware / SO**
- **Versão do código e commit hash**
- **Linguagem / runtime / flags de compilação**
- **Parâmetros do teste (resolução, carga, velocidade do alvo, iluminação)**
- **Métricas medidas (raw + agregadas)**
- **Notas de anomalias**

---

## Recomendações práticas
1. **Separar resultados por categoria de hardware** (microcontrolador vs SBC). Compare dentro da categoria e apenas comente diferenças entre categorias com cuidado.
2. **Automatizar a repetição**: scripts que rodem 10x e gerem CSV com timestamps para evitar erro humano.
3. **Sincronização de clocks**: se visão e controle estiverem em placas diferentes, sincronizar tempos (NTP ou pulso físico de sincronização).
4. **Medições físicas**: use osciloscópio para checar PWM quando suspeitar de diferenças de driver entre linguagens.
5. **Apresentação**: em tabelas no artigo, mostre média ± desvio; inclua colunas de "Condição" (p.ex. iluminação) para transparência.

---

Quer que eu gere também as **planilhas (CSV/Excel)** prontas para preenchimento com esses campos e fórmulas de análise (média, desvio, p-valor)?

