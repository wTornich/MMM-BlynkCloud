# MMM-BlynkCloud

O módulo MMM-BlynkCloud é uma abstração da plataforma de Internet das Coisas (IoT) Blynk para a interface do MagicMirror2. Seu objetivo é possibilitar e facilitar interações entre o espelho inteligente e microcontroladores como, por exemplo, os Esp8266 e Esp32.

Nesta primeira versão do MMM-BlynkCloud é possível criar botões, sliders, gráficos e labels (no formato de Widgets) personalizáveis que interajam com microcontroladores.

## 

Para utilizar este módulo, adicione-o à matriz de módulos no arquivo config/config.js:


    {
	    module: 'MMM-BlynkCloud',
	    position: 'top_right',
	    config: [
		    // Module configurations...
	    ]
    }

## 
## Exemplo de interface do módulo

### IMG - Interface do Módulo

##

## Utilização do módulo

Antes de apresentar as opções de configurações do módulo, é necessário entender como que acontece a comunicação da plataforma Blynk com um microcontrolador e a estrutura básica de configuração. Essas informações estão no site da plataforma disponível em [https://docs.blynk.io/en/](https://docs.blynk.io/en/), porém é válido apresentar uma noção básica para depois ser possível configurar o módulo.

### Entendendo a plataforma Blynk

Seguindo uma sequência de passos, primeiramente é necessário configurar um dispositivo.

![New Device & Token](https://github.com/wTornich/MMM-BlynkCloud/blob/main/imgs_md/device_&_token.png?raw=true)

Ao configurar um dispositivo, é gerado um Token de identificação que é utilizado toda vez que for necessário comunicar com ele. No projeto, o Token é utilizado no código que será carregado no microcontrolador e para fazer requisições na API da plataforma no código do módulo.

Em seguida já será possível adicionar recursos como botões, sliders, gráficos e labels. Na plataforma esses recursos são chamados de Widgets.

![Widgets](https://github.com/wTornich/MMM-BlynkCloud/blob/main/imgs_md/widgets_platform.png?raw=true)

Para que um Widget funcione, é necessário atrelar a ele um ou mais Datastreams, dependendo do Widget. Datastreams são variáveis configuráveis para estabelecer comunicação com os microcontroladores, seja diretamente com os pinos, utilizando Digital Pins e Analog Pins, ou indiretamente, utilizando Virtual Pins.
*OBS: Atualmente a plataforma suspendeu a utilização de Digital e Analog Pins.

### IMG - Datastreams

Depois de criar os Datastreams, basta atrelar eles aos Widgets desejados. Assim, o lado da plataforma já está configurado.

### Configurando microcontroladores e cenário testado

A plataforma Blynk gera um código base para poder configurar e testar os microcontroladores. Porém, nos arquivos deste repositório há uma pasta com dois exemplos de códigos utilizados para teste. Um deles é para ser utilizado com o Esp8266 e o outro para ser utilizado com o Esp32.

Vale ressaltar que foram utilizadas algumas bibliotecas:

 - WifiManager: Facilita a configuração de wifi, funcionando da mesma
   forma para os dois microcontroladores; 
  - BlynkSimpleEsp8266 e BlynkSimpleEsp32 - São as bibliotecas da própria plataforma que permite estabelecer comunicação com a mesma e usar as funções da Blynk para os microcontroladores;
 - Bibliotecas extras para utilizar sensores, como o DHT22 e o LDR.
