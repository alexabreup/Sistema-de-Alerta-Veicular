**Projeto: Sistema de Proteção Contra Esquecimento de Pessoas e Animais em Veículos Automotivos usando ESP32-S3**

---

### **1. Objetivo**
Desenvolver um sistema integrado para detectar a presença de pessoas ou animais em veículos e enviar alertas em tempo real, utilizando sensores, conectividade Wi-Fi/Bluetooth e algoritmos de IA.

---

### **2. Componentes Principais**
- **ESP32-S3**: Processamento, Wi-Fi, Bluetooth.
- **Sensores**:
  - **Peso**: Células de carga + amplificador HX711 (detecção de ocupação).
  - **Movimento**: Sensor radar RCWL-0516 (detecção de presença).
  - **Temperatura/Umidade**: DHT22 ou sensor digital I2C.
  - **Câmera**: Módulo OV2640 para verificação visual (opcional).
- **Conectividade**:
  - Módulo GPS NEO-6M (localização).
  - Buzzer e LEDs para alarme local.
- **Fonte de Energia**:
  - Regulador de tensão 12V → 3.3V (para uso em automóveis).
  - Bateria de backup (LiPo) com circuito de carga.

---

### **3. Arquitetura do Sistema**
![Diagrama de Blocos](https://via.placeholder.com/600x400?text=ESP32-S3+com+Sensores+GPS+e+C%C3%A2mera)

---

### **4. Funcionalidades Principais**
1. **Detecção Multissensorial**:
   - Sensores de peso + movimento + temperatura para confirmar presença.
   - Redução de falsos positivos via algoritmo de votação (mínimo 2 sensores ativos).

2. **Alertas Inteligentes**:
   - Notificações push via app móvel (Blynk/Firebase).
   - Alarme sonoro e visual no veículo.
   - Localização GPS em tempo real.

3. **Processamento de IA**:
   - Modelo TensorFlow Lite para detecção de presença via câmera (opcional).
   - Análise de anomalias em dados de sensores.

---

### **5. Etapas de Desenvolvimento**

#### **Fase 1: Hardware (2 semanas)**
- Montar protótipo com ESP32-S3, sensores e módulos.
- Integrar células de carga (HX711) e sensor radar.
- Configurar câmera OV2640 (se aplicável).

#### **Fase 2: Firmware (3 semanas)**
- **Sensoriamento**:
  - Leitura de peso, movimento e temperatura.
  - Calibração para evitar falsos positivos.
- **Conectividade**:
  - Configurar Wi-Fi/Bluetooth para envio de alertas.
  - Integração com GPS (UART).
- **Alarme Local**:
  - Ativar buzzer e LEDs ao detectar presença pós-desligamento.

#### **Fase 3: Aplicativo Móvel (2 semanas)**
- Desenvolver app com:
  - Notificações push (OneSignal/Firebase).
  - Visualização de dados em tempo real.
  - Histórico de alertas e localização GPS.

#### **Fase 4: Testes e Otimização (2 semanas)**
- Testes de precisão dos sensores em diferentes cenários.
- Validação de consumo de energia (modo deep sleep).
- Ajustes no algoritmo de votação e modelo de IA.

---

### **6. Cronograma**
| Fase          | Duração | Entregáveis                     |
|---------------|---------|---------------------------------|
| Hardware      | 2 sem   | Protótipo funcional             |
| Firmware      | 3 sem   | Código base com sensores/alertas|
| Aplicativo    | 2 sem   | Versão beta do app              |
| Testes        | 2 sem   | Relatório de validação          |

---

### **7. Orçamento Estimado**
| Item          | Custo (USD) |
|---------------|-------------|
| ESP32-S3      | 15,00       |
| Sensores      | 25,00       |
| Módulo GPS    | 10,00       |
| Câmera OV2640 | 12,00       |
| Componentes diversos | 20,00 |
| **Total**     | **82,00**   |

---

### **8. Desafios e Mitigações**
- **Consumo de Energia**: Usar deep sleep e bateria de backup.
- **Falsos Positivos**: Combinação de sensores + algoritmo de votação.
- **Processamento de IA**: Usar modelos leves (TensorFlow Lite Micro).

---

### **9. Resultado Esperado**
Sistema capaz de detectar presença em veículos com 98% de precisão, enviar alertas em até 30 segundos e operar por 7 dias em standby com bateria.