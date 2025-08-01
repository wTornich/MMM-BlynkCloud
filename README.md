# MMM-BlynkCloud

O módulo MMM-BlynkCloud é uma abstração da plataforma de Internet das Coisas (IoT) Blynk para a interface do MagicMirror2. Seu objetivo é possibilitar e facilitar interações entre o espelho inteligente e microcontroladores como, por exemplo, os Esp8266 e Esp32.

Nesta primeira versão do MMM-BlynkCloud é possível criar botões, sliders, gráficos e labels (no formato de Widgets) personalizáveis que interajam com microcontroladores.

Para utilizar este módulo, adicione-o à matriz de módulos no arquivo config/config.js:


    {
	    module: 'MMM-BlynkCloud',
	    position: 'top_right',
	    config: [
		    // Module configurations...
	    ]
    }

## Exemplo de interface do módulo

### IMG - Interface do Módulo
![Module Interface](https://github.com/wTornich/MMM-BlynkCloud/blob/main/imgs_md/module_interface.png?raw=true)
![Module Interface](https://github.com/wTornich/MMM-BlynkCloud/blob/main/imgs_md/MMM-BlynkCloud%20S1.jpg?raw=true)
![Module Interface](https://github.com/wTornich/MMM-BlynkCloud/blob/main/imgs_md/MMM-BlynkCloud%20S2.jpg?raw=true)

## Utilização do módulo

Antes de apresentar as opções de configurações do módulo, é necessário entender como que acontece a comunicação da plataforma Blynk com um microcontrolador e a estrutura básica de configuração. Essas informações estão no site da plataforma disponível em [https://docs.blynk.io/en/](https://docs.blynk.io/en/), porém é válido apresentar uma noção básica para depois ser possível configurar o módulo.

### Entendendo a plataforma Blynk

Seguindo uma sequência de passos, primeiramente é necessário configurar um dispositivo.

![New Device & Token](https://github.com/wTornich/MMM-BlynkCloud/blob/main/imgs_md/device_&_token.png?raw=true)

Ao configurar um dispositivo, é gerado um Token de identificação que é utilizado toda vez que for necessário comunicar com ele. No projeto, o Token é utilizado no código que será carregado no microcontrolador e para fazer requisições na API da plataforma no código do módulo.

Em seguida já será possível adicionar recursos como botões, sliders, gráficos e labels. Na plataforma esses recursos são chamados de Widgets.

![Widgets](https://github.com/wTornich/MMM-BlynkCloud/blob/main/imgs_md/widgets_platform.png?raw=true)

Para que um Widget funcione, é necessário atribuir a ele um ou mais Datastreams, dependendo do Widget. Datastreams são variáveis configuradas para estabelecer fluxos de dados e comunicação entre a plataforma e os microcontroladores, seja diretamente com os pinos, utilizando Digital Pins e Analog Pins, ou indiretamente, utilizando Virtual Pins.

### IMG - Datastreams

Depois de criar os Datastreams, basta atribuir eles aos Widgets desejados. Para que o módulo MMM-BlynkCloud funcione não precisa fazer essas atribuições aos Widgets da plataforma, ou seja, somente os Datastreams precisam ser configurados. 

### Configurando microcontroladores e cenário testado

A plataforma Blynk gera um código base para poder configurar e testar os microcontroladores. Entretanto, nos arquivos deste repositório há uma pasta com dois exemplos de códigos utilizados para teste. Um deles é para ser utilizado com o Esp8266 e o outro para ser utilizado com o Esp32.

Vale ressaltar que foram utilizadas algumas bibliotecas, além da biblioteca da plataforma Blynk (BlynkSimpleEsp8266 e BlynkSimpleEsp32):

 - WifiManager: Facilita a configuração de wifi nos microcontroladores; 
 - DHT22 para utilizar o sensor de temperatura e humidade;
 - LDR para utilizar o sensor de luminosidade;
 
## Utilização do módulo

### Estrutura do modulo


### MODULE STYLE
###### *IMG EXAMPLE*

| Properties | Description | Values | Values Type
|--|--|--|--|
| min_width | Minimum module width | Value in pixels | String
| min_height| Minimum module height | Value in pixels | String
| slider_devices | Configuration that indicates whether the devices will be displayed all together or collapsed with buttons to switch between them | true, false |Boolean


### DEVICES
###### *IMG EXAMPLE*

| Properties | Description | Values | Values Type
|--|--|--|--|
| devices | Device array | Devices list | Array


### DEVICE
###### *IMG EXAMPLE*

| Properties | Description | Values | Values Type
|--|--|--|--|
| token | Device token generated by the Blynk platform | Token text | String
| min_width | Minimum width of the panel containing the device's Widgets | Value in pixels | String
| min_height | Minimum height of the panel containing the device's Widgets | Value in pixels | String
| device_name | Device name that will appear at the top of the device panel | Device name | String
| widgets | Device Widget Array | Widgets list | Array

### WIDGET
###### *IMG EXAMPLE*

| Properties | Description | Values | Values Type
|--|--|--|--|
| type | Widget type | device_status, button, slider, gauge, label | String
| datastream | Blynk Platform DataStream ID Value | ID value | String
| style | Array of styles related to the Widget | Style list settings | Array

### WIDGET STYLES

##### DEVICE STATUS
###### *IMG EXAMPLE*
| Properties | Description | Values | Values Type
|--|--|--|--|
| min_width | Widget container minimum width | Value in pixels or percentage | String
| min_height | Widget container minimum height | Value in pixels or percentage | String
| icon_size | Status icon size | Value in pixels | String
| font_size | Font size | Value in pixels | String
| align | Widget alignment | left, center, right | String

##### BUTTON
###### *IMG EXAMPLE*
| Properties | Description | Values | Values Type
|--|--|--|--|
| min_width | Widget container minimum width | Value in pixels or percentage | String
| min_height | Widget container minimum height | Value in pixels or percentage | String
| label | Button name | Button name text | String
| label_font_size | Button name font size | Value in pixels | String
| label_align | Button name alignment | left, center, right | String
| icon_width | Button icon width | Button icon width value in pixels or percentage | String
| icon_height | Button icon height | Button icon height value in pixels | String
| icon_align | Button icon alignment | left, center, right | String

##### SLIDER
###### *IMG EXAMPLE*
| Properties | Description | Values | Values Type
|--|--|--|--|
||||
##### GAUGE
###### *IMG EXAMPLE*
| Properties | Description | Values | Values Type
|--|--|--|--|
||||
##### LABEL
###### *IMG EXAMPLE*
| Properties | Description | Values | Values Type
|--|--|--|--|
||||
