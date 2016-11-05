<!--
title: Instalando o MicroPython
-->

## Requisitos básicos
<img class="is-paragraph-floated-left has-250-width" src="/academy/courses/course-iot-esp8266-micropython/hero.png" alt="foto do nodemcu"> 

Para seguir esse curso você precisa de uma placa com o chip [ESP8266](https://pt.wikipedia.org/wiki/ESP8266). Ao longo do curso nós usaremos o [NodeMCU](http://www.nodemcu.com/index_en.html) porém outras placas com o ESP8266 funcionam também. A diferença entre essas placas é em geral qual versão do ESP8266 elas usam (o que afeta o quanto de memória flash você tem) e se elas já possuem uma interface para conexão com o computador.

No caso do NodeMCU, a placa é alimentada pela conexão USB que também serve para comunicação via terminal. Para seguir esse curso vamos conectar a placa ao seu computador via USB. Caso esteja utilizando outra placa com outro tipo de conexão, você precisará consultar o manual do fabricante para descobrir como conectá-la ao computador.

<article class="message is-info">
  <div class="message-header">
    Aviso
  </div>
  <div class="message-body">
    <p>
      O NodeMCU vem de fábrica com uma firmware baseada na linguagem <a href="https://lua.org">Lua</a>. Nesse curso iremos apagar essa firmware e substituí-la por <a href="https://micropython.org">uma baseada em Python 3</a>. Você pode fazer o processo inverso e retornar sua NodeMCU para Lua seguindo as instruções <a href="https://nodemcu.readthedocs.io/en/dev/en/flash/">da documentação oficial do NodeMCU</a>.
    </p>
  </div>
</article>

Por mais que o MicroPython seja baseado em Python 3, o programa para comunicação com o ESP8266 é baseado em Python 2 então você precisa ter o Python 2 instalado na sua máquina para fazer esse curso.

## Instalando o firmware
Nesta seção vamos instalar o esptool para então instalarmos o micropython no nodemcu. 

### Instalando o ESPTOOL
Como dito acima, o programa fornecido pela [Expressif, a fabricante do ESP8266](https://espressif.com/en/products/hardware/esp8266ex/overview) para fazer o flash do ESP8266 é feito em Python 2.7. O programa para fazer flash da firmware chama [ESPTOOL](https://github.com/themadinventor/esptool/) e a forma mais fácil de instalá-lo é via [pip](https://packaging.python.org/key_projects/#pip). 

<article class="message is-info">
  <div class="message-header">
    Aviso: Python 2, Python 3 e pip...
  </div>
  <div class="message-body">
    <p>
      Se sua instalação de Python padrão for a 3, você provavelmente tem um <code>pip</code> que está atrelado a essa versão, nesses casos utilize o programa chamado <code>pip2</code>. No caso inverso, temos normalmente um programa chamado <code>pip</code> para Python 2 e um <code>pip3</code> para Python 3.
    </p>
  </div>
</article>

No seu terminal, com Python 2.7 e o pip instalados, digite:

```
$ pip install esptool
```

Se tudo ocorrer bem, você terá o esptool instalado.

#### Video: exemplo de instalação do ESPTOOL no Mac OS X

<iframe src="https://player.vimeo.com/video/190308454" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

### Instalando o firmware
Agora que o esptool está instalado vamos fazer o flash da firmware no nodemcu. Isso irá apagar o firmware original e substituí-lo pelo micropython. A forma mais recomendada é apagar a memória antes de fazer o flash (para garantir o bom funcionamento da coisa).

#### Passo 1: Baixando o firmware do micropython.
Baixe o firmware [da página oficial do micropython](http://micropython.org/download#esp8266). **Atenção: você tem que baixar a firmware correta para a placa que você está usando, no nosso caso é a firmware para ESP8266.** Quando eu estava escrevendo esse curso, a firmware atual para o ESP8266 era a [```esp8266-20161017-v1.8.5.bin```](http://micropython.org/resources/firmware/esp8266-20161017-v1.8.5.bin).
 
#### Passo 2: Descobrindo em qual porta o NodeMCU está aparecendo.
Esta é a parte onde a maioria das pessoas encontra dificuldade. Existem vários fabricantes de NodeMCU e eles utilizam componentes eletrônicos diferentes um dos outros o que faz com que as placas necessitem de drivers diferentes dependendo do sistema operacional que você está utilizando. **O melhor a fazer é olhar a documentação da loja onde você comprou o NodeMCU**. A maioria dos NodeMCU circulando no Brasil são os V3 produzidos pela [Doctors of Intelligence & Technology](http://www.doit.am/) vulgo *doit.am*. Se você olhar sua placa e for feita por esses caras então você pode pegar o driver dela em:

**Reconhecendo um NodeMCU do doit.am**

<img src="/academy/courses/course-iot-esp8266-micropython/nodemcu_fundo.jpg" style="width: 30%;">

* [NodeMCU do Doit.am - Driver para Windows 10](http://en.doit.am/CH341SER.zip)
* [NodeMCU do Doit.am - Driver para Mac OS X](http://www.doit.am/CH341SER_MAC.ZIP)

Com a sua NodeMCU conectada via USB ao seu computador uma nova interface ou porta irá surgir.

## Testando o firmware

### Terminal

### Rede
