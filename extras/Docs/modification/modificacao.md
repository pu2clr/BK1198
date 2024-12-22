# PASSOS PARA MODIFICAR UM RÁDIO COMERCIAL BASEADO NO BK1198


**Modificando Receptores Comerciais Baseados no DSP BK1198: Guia Prático**  

A modificação de receptores comerciais baseados no DSP BK1198 é uma experiência empolgante para entusiastas de rádio e desenvolvedores. Essa prática permite expandir a capacidade de rádios AM/FM, adicionando a recepção de Ondas Curtas (SW). No entanto, é essencial seguir algumas recomendações para garantir o sucesso da modificação e minimizar riscos.  

### 1. Desprendimento: Esteja Ciente dos Riscos  

Antes de iniciar qualquer modificação, é importante ter em mente que essa operação envolve **riscos de danos irreparáveis** ao dispositivo. A manipulação de circuitos eletrônicos delicados pode resultar na perda total do rádio. Por isso, **proceda com cautela** e esteja preparado para lidar com possíveis falhas.  

### 2. Conhecimento é Fundamental  

Antes de colocar a mão na massa, busque o máximo de conhecimento possível sobre o **BK1198**. Recomendo a leitura detalhada do **datasheet** do dispositivo, pois ele contém informações técnicas essenciais. Para acessar esse documento, uma simples busca no Google utilizando a string **"BK1198 Datasheet"** deve ser suficiente. A compreensão das especificações do DSP é um passo crítico para realizar a modificação com segurança.  

### 3. Localizando os Pinos-Chave  

Após desmontar o rádio, é necessário localizar **o pino 1 e o pino 15 do BK1198** na placa do dispositivo. Esses pinos serão fundamentais para o processo de modificação, pois são responsáveis pela seleção das bandas de frequência.  

### 4. Desabilitação do Banco de Resistores  
O próximo passo é **desabilitar o banco de resistores** que compõe o divisor de tensão responsável pela seleção original de bandas (AM/FM). Esse circuito impede que novas bandas, como Ondas Curtas, sejam sintonizadas.  

### 5. Remoção da Chave de Onda Original  

Se o rádio possuir uma chave de onda (switch AM/FM), considere **removê-la**. A substituição por uma chave personalizada permitirá a inclusão da faixa de Ondas Curtas.  

### 6. Montagem da Nova Chave de Onda  

Monte a nova chave de onda conforme o diagrama que será apresentado a seguir. Essa chave permitirá alternar entre diferentes bandas (AM, FM e SW).  

### 7. Conexão da Nova Chave de Onda  

Agora é hora de conectar a nova chave de onda na placa do rádio. Siga as instruções abaixo:  

- **Conector central da chave de onda** → Conecte ao **pino 15 do BK1198**.  
- **Fio do início da chave de onda** → Ligue ao **terra da placa do rádio**.  
- **Fio do final da chave de onda** → Conecte ao **pino 1 do BK1198**.  

### Finalizando a Modificação  

Após realizar essas conexões, o rádio estará pronto para operar nas novas faixas de frequência, convertendo-se em um **receptor AM/FM e SW**. Esses são os procedimentos básicos para realizar essa modificação com sucesso.  


**Considerações Finais**  

Após concluir com sucesso os procedimentos de modificação, é provável que você se surpreenda ao perceber que o rádio alterado é capaz de sintonizar estações remotas em ondas curtas. No entanto, é importante destacar que a ausência de filtros de passagem de banda, ou a presença de filtros pré-configurados para AM e FM, pode limitar a recepção de diversas formas.  

Essas limitações podem se manifestar de algumas maneiras:  
- **Interferência de estações próximas** – É possível que você ouça sinais distorcidos de estações de FM locais ou até mesmo capte com clareza o áudio de uma estação de ondas médias.  
- **Sobreposição de sinais** – Estações de FM próximas podem interferir nas faixas de ondas curtas, causando distorções em determinadas frequências.  

Se essas interferências ocorrerem, será necessário **adicionar filtros de passagem de banda** nos circuitos de AM e FM do receptor. O datasheet do BK1198 oferece algumas recomendações sobre como implementar esses filtros de forma eficaz.  

Caso o rádio já possua um filtro na entrada, a recepção de ondas curtas pode ser comprometida, resultando em um sinal muito fraco. Se isso ocorrer, será necessário **modificar o circuito da antena** para contornar ou substituir esse filtro, garantindo uma captação adequada das faixas de ondas curtas.  

**Observação:** Em meus experimentos, **não enfrentei problemas de sinal fraco**. Entretanto, há uma estação de FM próxima à minha residência que causa interferência em algumas frequências de ondas curtas. Contudo, dada a natureza do experimento, essa interferência não representa um problema significativo.  

A experiência de modificar e explorar o potencial do rádio é enriquecedora, e lidar com essas limitações faz parte do aprendizado.


Boa sorte e bons experimentos!

