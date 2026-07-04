Traducción de direcciones de red (NAT), para utilizar direcciones IP privadas

La mayoría de las redes internas, desde grandes empresas hasta redes domésticas, utilizan direcciones IPv4 privadas para dirigirse a todos los dispositivos internos (intranet), incluidos los hosts y enrutadores. Sin embargo, las direcciones privadas no son enrutables globalmente.

En la figura, las redes de clientes 1, 2 y 3 están enviando paquetes fuera de sus redes internas. Estos paquetes tienen una dirección IPv4 de origen que es una dirección privada y una dirección IPv4 de destino que es pública (enrutable globalmente). Los paquetes con una dirección privada deben filtrarse (descartarse) o traducirse a una dirección pública antes de reenviar el paquete a un ISP. 