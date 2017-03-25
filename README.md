# iceZUM Alhambra B01-026
En este repositorio exploraremos las posibilidades, con pruebas y ejemplos, de mi ___iceZUM Alhambra nº26___.
Es una de las placas pertenecientes a la primera tirada realizada en [FPGAWars](http://fpgawars.github.io/) (revisión v1.1).

Vamos a explorar las nuevas posibilidades no documentadas de la placa y llevarla al límite cuando sea posible. Para ello nos basaremos en los _datasheet_ de los circuitos integrados que la componen.
Los primeros progresos se han obtenido en la _reconfiguración_ de la FPGA (iCE40HX) que es el corazón de la ___iceZUM Alhambra___.

El chip iCE40HX de _Lattice_ es una FPGA volátil, es decir, al perder la alimentación, pierde su configuración interna de conexiones que conforman el circuito, es por eso que necesita de una PROM (Programable ROM) donde guardar dicha configuración (_bitstream_) y descargarla en la FPGA cada vez que se produce un _"hard-reset"_.

Este chip PROM en la **_iceZUM Alhambra_** es una memoria tipo flash (el chip _N25Q032A_) se comunica vía SPI con la FPGA y el FTDI (_FT2232H_, interfaz con el USB del PC).

> Incluir gráfico del esquema.

Esta memoria, en la _iceZUM Alhambra_, tiene mucha mayor capacidad de lo necesario para guardar el _bitstream_ que necesita la FPGA de Lattice. Surge así la posibilidad de utilizar la memoria restante como memoria de propósito general para la FPGA.

Sim embargo, es el chip _iCE40HX_ el que nos da la posibilidad de dar un uso inmediato a esta mayor capacidad, ya que mediante unos pines externos nos permite elegir entre distintos _bitstreams_ guardados en la misma memoria (lo que se conoce en la documentación como _"Cold Boot"_). Este proceso puede verse esquematizado en la siguiente figura.

> Incluir esquema del proceso "Cold/Warm Boot".

Para acceder al código, las pruebas y una mayor información, sigue los siguientes enlaces.

- [***Cold Boot***](https://github.com/juanmard/icezum/tree/master/ColdBoot)
- [***Warm Boot***](https://github.com/juanmard/icezum/tree/master/WarmBoot)

