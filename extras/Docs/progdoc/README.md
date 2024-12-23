


Endereço I2C = 0x80

Registradores:

REG0(DeviceID),0000000000001320
REG1(ChipID),0000000000001080
REG2(PowerCfg),0000000000000281
REG3(Channel),0000000000000000
REG4(SysConf1),000000000000D823
REG5(SysConf2),000000000000001F
REG6(SysConf3),000000000000280E
REG7(SysConf4),0000000000004101
REG8(SysConf5),0000000000008C90
REG9(StatusSNR),0000000000000000
REG10(StatusRSSI),0000000000000000
REG11(ReadChannel),0000000000000000
REG12(StatusBAND),0000000000000000
REG13(DigTest1),00000000000013C1
REG14(DigTest2),0000000000006DF0
REG15(DigTest3),000000000000002F
REG16(DigTest4),0000000000001A1C
REG17(DigTest5),0000000000003000
REG18(DigTest6),0000000000001000
REG19(DigTest7),00000000000023A5
REG20(DigTest8),0000000000000000
REG21(DigTest9),0000000000000000
REG22(MTP1),0000000000003A71
REG23(MTP2),000000000000231B
REG24(MTP3),0000000000004A15
REG25(MTP4),000000000000431A
REG26(MTP5),0000000000004A15
REG27(MTP6),0000000000007F6A
REG28(FM2_FREQ1),00000000000002F8
REG29(FM2_FREQ2),0000000000000398
REG30(FM3_FREQ1),0000000000000280
REG31(FM3_FREQ2),0000000000000366
REG32(MW1_FREQ1),0000000000000034
REG27(MW1_FREQ2),00000000000000AB
REG34(MW2_FREQ1),000000000000003A
REG35(MW2_FREQ2),00000000000000B4
REG36(MW3_FREQ1),00000000000001F8
REG37(MW3_FREQ2),00000000000006AE
REG38(SW1_FREQ1),0000000000000163
REG39(SW1_FREQ2),00000000000001CF
REG40(SW2_FREQ1),00000000000001AB
REG35(SW2_FREQ2),000000000000023D
REG42(SW3_FREQ1),0000000000000218
REG43(SW3_FREQ2),000000000000027D
REG44(SW4_FREQ1),000000000000027D
REG45(SW4_FREQ2),0000000000000302
REG46(SW5_FREQ1),000000000000039E
REG47(SW5_FREQ2),0000000000000435
REG48(SW6_FREQ1),0000000000000405
REG49(SW6_FREQ2),00000000000004BE
REG50(SW7_FREQ1),00000000000004EF
REG51(SW7_FREQ2),00000000000005A8
REG52(SW8_FREQ1),00000000000005B6
REG53(SW8_FREQ2),0000000000000666
REG54(SW9_FREQ1),00000000000006A2
REG55(SW9_FREQ2),0000000000000757
REG56(SW10_FREQ1),00000000000007E3
REG57(SW10_FREQ2),00000000000008A7
REG58(SW11_FREQ1),0000000000000257
REG59(SW11_FREQ2),0000000000000708
REG60(SW12_FREQ1),000000000000031F
REG61(SW12_FREQ2),0000000000000708
REG62(Analog0),0000000000004CA2
REG63(Analog1),0000000000008E20
REG64(Analog2),0000000000000200
REG65(Analog3),0000000000000000
REG66(FM Analog4),000000000000A8E4
REG67(Analog5),0000000000003264
REG66(AM Analog6),000000000000A8E4

1.2 Circuito Ressonante na Entrada de Antena FM

Pino Relacionado: FMI

Na entrada de antena do receptor FM, geralmente é conectado um circuito LC ressonante ligado ao terra para melhorar o desempenho de recepção.

Normalmente, a frequência ressonante do circuito LC externo é ajustada para o ponto médio da banda de frequência, por exemplo, 97 MHz. Para essa frequência, o valor típico do indutor é de 100 nH e o capacitor é de 24 pF.

No entanto, na prática, há uma capacitância parasita de aproximadamente 6 pF no pino de entrada (incluindo a capacitância interna do chip e a capacitância em relação ao terra da antena do fone de ouvido). Por esse motivo, recomenda-se que o capacitor ressonante externo tenha um valor de 18 pF.

Em resumo, ao utilizar um indutor externo de 100 nH, o valor do capacitor deve ser ajustado conforme as condições reais de uso para otimização do desempenho.


**1.3 Circuito LNA Externo de Ondas Curtas e Circuito AM**  

**Pinos Relacionados:** RFGND, AMI, LNA_EN  

Para recepção de ondas curtas, geralmente utiliza-se uma **antena telescópica**. É necessário adicionar um **LNA (Amplificador de Baixo Ruído)** externo para amplificar o sinal na entrada. O diagrama do circuito é mostrado abaixo.  

Ao alternar para o modo de ondas curtas (**SW**), o pino **LNA_EN** emite um sinal de nível alto para a base do amplificador externo (**9018**).  

- O componente **FB1** no diagrama é usado para isolar o sinal de **FM**.  
- O capacitor **C3 = 33 pF** serve para isolar o sinal de **SW**.  
- O capacitor **C22 = 1 pF** tem duas funções:  
  1. Reduz o ganho de amplificação do sinal de ondas curtas, evitando a saturação do sinal que entra no **BK1198**.  
  2. Isole o sinal de **AM** para garantir que a recepção de **AM** não seja afetada.  

Para recepção de **AM**, geralmente utiliza-se uma **antena de bastão de ferrite**. Recomenda-se usar um bastão maior, dentro dos limites do tamanho do dispositivo. A antena deve ser mantida afastada do chip **BK1198**, de outros circuitos e de objetos metálicos para minimizar interferências.


**1.4 Seleção de Modo: Fonte dos Registradores e Circuito de Interface I2C/IRQ**  

**Pinos Relacionados:** MODE, SCLK, SDIO, IRQ/BAND_IND1  

A configuração dos registradores internos do **BK1198** pode ser obtida de duas fontes:  
1. **Valores padrão do SPI interno**  
2. **Valores armazenados na memória interna MTP (Multi-Time Program – gravação múltipla)**  

As duas linhas do **I2C** podem ser configuradas para operar como uma interface I2C comum ou para indicar:  
- **STEREO** (indicação de estéreo)  
- **STATION** (indicação de estação válida)  

A seleção entre esses modos é determinada pela tensão de entrada do pino **MODE**. Para detalhes específicos, consulte a tabela correspondente.


Quando a **porta I2C** está habilitada, é necessário conectar dois resistores de pull-up ao MCU externo. Isso permite que o MCU controle o **BK1198** e grave as configurações de **MTP**.  

Quando a **porta I2C** está desabilitada, os pinos **SCLK** e **SDIO** são usados como indicadores, emitindo um sinal de nível alto:  
- **SCLK** indica **estéreo**  
- **SDIO** indica uma **estação válida**  

O pino **IRQ/IND1** funciona como um pino de solicitação de interrupção. Primeiramente, é necessário verificar a configuração dos registradores internos, garantindo que o pino **IRQ/IND1** esteja configurado como saída de interrupção (**REG17H<15> = 0**). Por padrão, esse pino é configurado como saída de interrupção ao ligar o dispositivo.  

Quando operando como um pino de interrupção, ele gera uma transição de **borda de descida** (falling edge) para o MCU ao concluir a definição de uma frequência. O MCU então lê o valor da frequência atual através do I2C.


**1.5 Circuito de Alimentação e Chave de Liga/Desliga (PWD)**  

**Pino Relacionado:** PWD  

O BK1198 possui três modos de alimentação e chaveamento para ligar e desligar o dispositivo:  
1. **Modo de Ligação Direta (Power-On ao Energizar)**  
2. **Modo de Chave Única (Single Button)**  
3. **Modo de Chave Dupla (Dual Button)**  

Esses três modos não requerem nenhuma configuração nos registradores internos. A seleção do modo é feita apenas por modificações no circuito externo.


**1.5.1 Modo de Ligação Direta (Power-On ao Energizar)**  

Nesse modo, um interruptor externo é utilizado para controlar diretamente a tensão de alimentação do **BK1198**.  

- Quando a alimentação é conectada, o chip liga automaticamente.  
- O pino **PWD** precisa apenas ser conectado a um circuito de atraso **RC** (resistor-capacitor).


**1.5.2 Modo de Chave Única**  

O modo de chave única permite controlar o chip alternando entre o modo de espera (standby) e o modo de operação normal através de um botão externo.  

- Quando a alimentação é conectada, o chip entra inicialmente no **modo de espera**.  
- Ao pressionar o botão, o chip muda para o **modo de operação normal**.  
- Ao pressionar o botão novamente, o chip retorna ao **modo de espera**.  
- Pressionando o botão repetidamente, o chip alternará continuamente entre os dois modos.


**1.5.3 Modo de Chave Dupla**  

O modo de chave dupla permite controlar o estado de operação do chip usando dois botões externos.  

- Quando a alimentação é conectada, o chip entra inicialmente no **modo de espera (standby)**.  
- Pressionar o botão **S1 (ON)** faz com que o chip entre no **modo de operação normal**.  
- Pressionar o botão **S2 (OFF)** coloca o chip de volta no **modo de espera**.  
- Se **S1** for pressionado enquanto o chip já estiver no modo de operação normal, ou **S2** for pressionado enquanto estiver no modo de espera, o sistema **mantém seu estado atual** sem alterações.


**1.6 Circuito de Controle de Volume**  

**Pino Relacionado:** VOL  

O controle de volume possui três modos:  
1. **Modo de Controle por Nível**  
2. **Modo de Controle por Chave Dupla**  
3. **Modo de Controle por Encoder Rotativo**  

A seleção do modo de controle de volume deve ser configurada nos registradores **REG16H[7:6] = REG22[7:6]**. A configuração padrão é o **modo de chave dupla**.  

---

**1.6.1 Modo de Controle por Nível**  

O controle por nível ajusta o volume detectando o nível de tensão no pino de entrada **VOL**.  

- Nesse modo, o chip possui **dois valores fixos de volume**. Para ajustes mais precisos, é necessário utilizar um amplificador de áudio externo.  
- Quando a entrada **VOL** está em nível **alto**, o volume de saída é o valor máximo definido no registrador (valor padrão).  
- Quando a entrada **VOL** está em nível **baixo**, o volume de saída é **6 dB** menor do que o valor padrão do registrador.  

---

**1.6.2 Modo de Controle por Chave Dupla (Configuração Padrão)**  

O controle por chave dupla permite ajustar o volume através de dois botões externos:  
- Um botão é definido como **aumentar volume (VOL+)**.  
- O outro botão é definido como **diminuir volume (VOL-)**.  

- Cada vez que o botão **VOL+** é pressionado, o volume aumenta em **2 dB** até atingir o volume máximo.  
- Cada vez que o botão **VOL-** é pressionado, o volume diminui em **2 dB** até atingir o volume mínimo.

**1.6.3 Modo de Controle por Encoder Rotativo**  

O controle por encoder funciona gerando dois pulsos defasados através de um circuito de decodificação interno quando o encoder é girado.  

- A direção de rotação do encoder determina a relação de fase entre os dois pulsos de saída (**adiantado em 1/4 de fase** ou **atrasado em 1/4 de fase**), o que permite identificar se o volume deve **aumentar ou diminuir**.  
- Se a direção de rotação estiver invertida em relação à desejada, basta trocar os valores de **R32** e **R33**.


**2. Seleção de Banda e Sintonia de Frequência do BK1198**  




**2.1 Definição de Bandas do BK1198**  

O **BK1198** oferece **18 bandas diferentes**, que incluem:  
- **3 bandas de FM (modulação em frequência)**  
- **3 bandas de AM (modulação em amplitude)**  
- **12 bandas de SW (ondas curtas)**  

A seleção das diferentes bandas é feita utilizando uma rede divisora de tensão com resistores de precisão comum (**5%**). O valor total da resistência da rede de seleção de bandas é fixo em **360 kΩ** (resistor de **TUNE1 ao terra**).  

- A banda **FM1** é uma banda fixa.  
- As outras bandas podem ter seus pontos de frequência inicial e final personalizados através do **MTP**.  

Aqui está a tradução da tabela de definição de bandas do BK1198 em formato Markdown:

```markdown
# Definição de Bandas - BK1198

| No BAND | Banda Name | Faixa de Frequência | Espaçamento de Canais |  Resistência | 
| ------- |------------|---------------------|-----------------------| -------------|
|  1      | FM1        | 87 - 108 MHz        | 100 kHz               |  10          | 
|  2      | FM2        | 87 - 108,5 MHz      | 100 kHz               |  30          |
|  3      | FM3        | 64 - 108 MHz        | 50 kHz                |  50          |
|  4      | AM1        | 510 - 1730 kHz      | 9/10 kHz              |  70          |
|  5      | AM2        | 513 - 1629 kHz      | 9/10 kHz              |  90          |
|  6      | AM3        | 513 - 1730 kHz      | 1 kHz                 | 110          |
|  7      | SW1        | 4,70 - 5,10 MHz     | 5 kHz                 | 130          |
|  8      | SW2        | 5,50 - 6,50 MHz     | 5 kHz                 | 150          |
|  9      | SW3        | 6,70 - 7,70 MHz     | 5 kHz                 | 170          |
| 10      | SW4        | 9,10 - 10,1 MHz     | 5 kHz                 | 190          |
| 11      | SW5        | 11,4 - 12,3 MHz     | 5 kHz                 | 210          |
| 12      | SW6        | 13,3 - 14,3 MHz     | 5 kHz                 | 230          |
| 13      | SW7        | 14,9 - 16,0 MHz     | 5 kHz                 | 250          |
| 14      | SW8        | 17,0 - 18,1 MHz     | 5 kHz                 | 270          |
| 15      | SW9        | 21,1 - 22,1 MHz     | 5 kHz                 | 290          |
| 16      | SW10       | 2,70 - 10,25 MHz    | 5 kHz                 | 310          |
| 17      | SW11       | 9,80 - 22,2 MHz     | 5 kHz                 | 330          |
| 18      | SW12       | 7,80 - 16,2 MHz     | 5 kHz                 | 350          |


**Observação:**
- A banda FM1 é fixa.  
- As demais bandas podem ser configuradas por meio do MTP (Multi-Time Programmable) para ajustar a frequência inicial e final dentro dos limites especificados no datasheet.
``` 

Se precisar de mais alguma seção traduzida ou formatada em Markdown, é só avisar!


**Observação:** A faixa de frequência personalizada não pode ultrapassar os limites mínimos e máximos definidos no datasheet.



2.2 Modos de Seleção de Banda e Indicação FM/AM do BK1198

Pinos Relacionados: AM/FM, BAND, IRQ/BAND_IND1, BAND_IND2.

O BK1198 possui quatro modos de seleção de banda:

Modo de Seleção por Chave de Banda
Modo de Seleção por Nível e Chave de Banda
Modo de Seleção por Tecla Única e Chave de Banda
Modo de Seleção por Dupla Tecla e Chave de Banda
Os quatro modos são configurados através dos registradores REG16H[5:4] e REG22[5:4]. Os valores de configuração podem ser alterados via MTP ou escritos diretamente através do I2C.

2.2.1 Modo de Seleção por Chave de Banda (Configuração Padrão)

Por padrão, o registrador está configurado para exigir apenas a chave de banda.

A rede de resistores abaixo corresponde a todos os 18 bandas. Caso o número de bandas seja reduzido, o valor do resistor de cada banda até o terra deve permanecer inalterado.

O valor total do resistor deve ser mantido constante em 360 kΩ (resistor de TUNE1 até o terra).



2.2.2 Modo de Seleção por Nível e Chave de Banda

Nesse modo, o chip detecta o nível do pino AM/FM.

Se o nível desse pino for baixo (LOW), o chip sempre entrará em FM1, FM2 ou FM3, independentemente da tensão no pino BAND (a seleção entre FM1, FM2 ou FM3 é configurada pelo registrador REG17H<14:13>, sendo FM1 o valor padrão).
Se o nível do pino for alto (HIGH), o chip entrará nas faixas de frequência AM e SW. A faixa específica será determinada pela tensão detectada no pino BAND (a seleção de banda é feita por meio de um seletor deslizante de bandas).


2.2.3 Modo de Seleção por Tecla Única e Chave de Banda

Nesse modo, o chip detecta o estado do botão conectado ao pino AM/FM.

Cada vez que o botão é pressionado, o chip alterna entre a banda FM (a seleção da banda FM pode ser configurada através do registrador REG17H<14:13>, com FM1 como padrão) e as bandas AM e SW.
A banda de operação é determinada pela tensão detectada no pino BAND (através de um seletor deslizante de bandas).


2.2.4 Modo de Seleção por Dupla Tecla e Chave de Banda

Nesse modo, o chip detecta o estado dos botões conectados ao pino AM/FM.

Ao pressionar o botão FM (nível baixo), o chip opera na banda 3 (FM3).
Ao pressionar o botão AM (nível alto), o chip entra nas bandas AM e SW. A banda específica é determinada pela tensão detectada no pino BAND (através de um seletor deslizante de bandas).

2.2.5 Indicação FM/AM

Os pinos IRQ/BAND_IND1 e BAND_IND2 são utilizados para indicar se o chip está no modo FM ou AM.

Primeiramente, é necessário verificar a configuração do registrador interno, garantindo que o pino IRQ/BAND_IND1 esteja configurado como saída de indicação de banda (REG17H<15> = 0, padrão de fábrica).

O circuito de hardware deve ser projetado conforme a Figura 17.

Quando BAND_IND1 emite nível alto e BAND_IND2 = 0, o chip está em modo FM.
Quando BAND_IND1 emite nível alto e BAND_IND2 = 1, o chip está em modo AM.
Além disso, o pino BAND_IND1 também pode ser utilizado para controlar o sinal de chaveamento de um amplificador de áudio externo, ajudando a eliminar o ruído de "pop" ao ligar o dispositivo.

2.3 Sintonia de Frequência do BK1198

Pinos Relacionados: TUNE1, TUNE2.

O BK1198 possui três modos de sintonia de frequência:

Modo de Sintonia por Potenciômetro (PVR)
Modo de Sintonia por Encoder Rotativo
Modo de Escrita Direta de Frequência via I2C
Esses três modos são configurados através dos registradores REG16H[3:2] e REG22[3:2] por meio do campo CHAN_MOD.

Os valores de configuração podem ser alterados através de MTP ou escritos diretamente via I2C.

2.3.1 Modo PVR (Configuração Padrão)

Nesse modo, o pino TUNE2 utiliza um ADC interno para detectar o estado de ajuste do PVR.

A frequência de operação atual é calculada e escrita com base nos valores ajustados.


2.3.2 Modo de Sintonia por Encoder Rotativo

O princípio de funcionamento do encoder é semelhante ao de um encoder de controle de volume.

Ao girar no sentido horário (em velocidade normal), a frequência de operação aumenta em 1 em relação à frequência atual.
Ao girar no sentido anti-horário, a frequência diminui em 1.
Se a direção de rotação estiver invertida em relação à desejada, basta trocar os valores de R46 e R47.

Para melhorar a experiência de uso em bandas com muitas frequências, é implementada uma função de detecção de velocidade de rotação.

Quando a velocidade de rotação excede um determinado limite, a frequência muda em incrementos de 5 a cada giro.

2.3.3 Modo de Escrita de Frequência via I2C

Nesse modo, o chip não responde mais à seleção de banda por chave.

A frequência de operação é totalmente controlada por um dispositivo externo através de comandos enviados via I2C.




**3 Gravação de MTP**  

Para realizar a gravação do **MTP**, o hardware deve conectar o **MCU externo** à interface **I2C** do **BK1198** através dos pinos **SCLK** e **SDIO** (com resistores de pull-up). O pino **MODE** deve habilitar o I2C (conectado a **0,375 \* VCC** ou **0,625 \* VCC**). Com a alimentação e o circuito do cristal, a gravação do **MTP** pode ser realizada.  

No processo de software, primeiro utilize o arquivo executável **“BK1198 Control Software_*.exe”** para importar o arquivo padrão **BK1198_default.txt**. Faça as modificações necessárias nos registradores e salve como **BK1198_updated.txt**.  

O novo arquivo de **MTP**, **BK1198_updated.txt**, deve ser gravado usando o executável **“BK1198 Download Software_*.exe”**. Recomenda-se executar este software em **Windows XP** ou **Windows 7**. Em outros sistemas operacionais, o reconhecimento pode falhar.  

Para detalhes do código-fonte da gravação de **MTP**, consulte o diretório **“BK1198 MTP Download Reference Code”**.  

---

### **3.1 Diagrama de Gravação de MTP**  

No hardware de gravação de **MTP**, a interface **I2C** do **MCU externo** conecta-se ao **BK1198** nos seguintes pinos:  
- **PIN9 = SCLK**  
- **PIN10 = SDIO**  

O MCU padrão utilizado é o **Silicon Labs C8051F320**, e a interface I2C corresponde aos pinos **P2.2** e **P2.3**, com resistores de pull-up de **10K** em cada um.  

Há um botão conectado ao MCU, ligado ao pino **START (P0.4)**. O pino **P0.4** é configurado por padrão como entrada com pull-up. Ao pressionar o botão, detecta-se a transição para o nível baixo, iniciando o processo de download de **MTP**.  

O pino **P0.6** conecta-se a um LED verde. Quando o nível lógico está **baixo**, o LED acende, indicando que o download de **MTP** foi concluído com sucesso.  

O pino **P0.7** conecta-se a um LED vermelho. Quando o nível lógico está **baixo**, o LED acende, indicando que o download de **MTP** falhou.  

O programa gravado na **Flash** do **MCU** é o **BK1198_Tool_FW_*.omf**. Por padrão, essa **Flash** já vem gravada. Caso precise regravá-la, consulte a documentação do **Silicon Labs C8051F320**.


4. Controle do BK1198 por MCU

4.1 Diagrama de Controle do BK1198 por MCU





**4.2 Ajuste Manual e Exibição Numérica no MCU**

O pino **IRQ/IND1** é o pino de solicitação de interrupção. Primeiramente, é necessário verificar a configuração do registrador interno do BK1198, garantindo que a função do pino **IRQ/IND1** esteja configurada como saída de interrupção (**REG17H<15>=0**). (Por padrão, este pino está configurado como saída de interrupção).

Quando configurado como saída de interrupção, ao concluir a definição da frequência, um sinal de pulso positivo é enviado ao MCU. O MCU responde a este sinal de solicitação de interrupção lendo, via I2C, o valor do ponto de frequência ajustado pelo **PVR**.

1. **Seleção de Modo** – Consulte “Seleção de Modo: Fonte do Registrador e Circuito de Interface I2C/IRQ”.
2. Ao utilizar o ajuste manual de sintonia por **PVR**, o **IRQ** emitirá um sinal de interrupção. O programa no MCU irá ler o valor da banda no registrador **REG12** (**REG12[14:9]**) e o valor do canal (**REG12[8:0]**). O valor de banda é usado para determinar a faixa de operação atual.

A relação entre Banda, Canal e Frequência (ponto de frequência de operação atual) é a seguinte:
**Frequência = canal * intervalo de canal da banda + frequência inicial da banda**

**Observações:**
1. A unidade do intervalo de canal da banda e da frequência inicial da banda deve ser a mesma.
2. Os valores padrão de frequência inicial e final de cada banda, bem como o intervalo de canal da banda, podem ser encontrados na “Tabela de Definição de Bandas do BK1198”. Os clientes também podem modificar os valores iniciais por meio do MCU para personalizar a frequência inicial e final da banda (os valores definidos não podem ultrapassar o limite mínimo e máximo de frequência de operação especificados no datasheet).
3. A frequência de operação calculada com base na fórmula acima representa a frequência de operação definida pelo **PVR** e não considera o desvio de frequência causado pelo **AFC**.


Aqui está a tradução do texto solicitado:  

---

**4.3 Sintonização Automática com o MCU**  

Ao realizar a sintonização automática com o MCU, o programa do MCU deve primeiro alterar o valor de **CHAN_MODE[1:0]** no registrador **REG22** de **0** para **2** (alterando o controle de **PVR** para controle via **I2C**).  

Em seguida, o programa altera o valor de **BAND_I2C[5:0]** no registrador **REG13** para o valor da banda que será escaneada (**1~15**).  

Depois disso, o programa modifica o valor de **CHAN_I2C[14:0]** no registrador **REG3**, variando do ponto de frequência inicial da banda até o ponto de frequência final.  

A cada vez que o valor de **CHAN_I2C[14:0]** for alterado, é necessário modificar o valor de **TUNE_I2C** no registrador **REG3** de **0** para **1** e depois retornar para **0**. Após um atraso de aproximadamente **50 ms**, o programa pode ler os valores de **AFC[8:0]** e **SNR[6:0]** no registrador **REG9** e o valor de **RSSI[6:0]** no registrador **REG10** para determinar se a frequência atual corresponde a uma estação válida.  

(O critério de validação pode ser baseado em outros chips de recepção **FM/AM** da **BEKEN**).  

Se for uma estação válida, o MCU armazena a frequência correspondente na memória e, em seguida, continua alterando a frequência até que o processo de escaneamento atinja o ponto final definido.  


5. Considerações para Layout de PCB

Maximize a área de aterramento. As entradas FMI e AMI devem manter o plano de terra limpo. Os indutores e capacitores do circuito ressonante na entrada FM devem ser colocados o mais próximo possível do pino de entrada FMI do chip.
Os capacitores de desacoplamento da fonte de alimentação devem ser posicionados o mais próximo possível do chip.
O cristal de 32 kHz deve ser colocado o mais próximo possível do chip.
As trilhas de TUNE1 e TUNE2 devem ser roteadas em paralelo e próximas uma da outra.
O bastão de ferrite deve ser posicionado a uma certa distância do chip para evitar interferências internas. Ele também deve estar afastado de outras fontes de ruído do sistema (como baterias). Se possível, uma camada de plano de terra limpa deve ser colocada entre a antena de ferrite e o restante do sistema para isolamento.
Evite o uso de componentes de alta emissão de ruído, como amplificadores classe D (Class-D PA) e fontes de alimentação comutadas. Caso não seja possível evitar, esses componentes devem ser posicionados longe dos circuitos de recepção de baixo ruído ou em lados opostos da PCB.
O plano de terra sob o LNA externo para SW deve ser o mais contínuo possível, mantendo um plano de terra limpo.






