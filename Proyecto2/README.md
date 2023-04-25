# Cambios en el proyecto 2

Se detectó que faltaron 2 switches que son necesarios para poder configurar las ips virtuales de las sedes Central y Jutiapa.

La sede Jutiapa quedaría así:

![Alt text](img/Captura%20de%20pantalla%202023-04-25%20105444.png)

Lo que se agregó fue el switch entre J1 y J2 y ESW1. Al switch no se le configura nada, las ips de e0/0 de los routers J1 y J2 siguen siendo las mismas.

La ip de 0/2 de ESW1 quedará definida como 192.167.XX.4. Para toda esta red usemos una máscara de subred /24.

Para configurar una ip en un switch de capa 3 se hace así.

    enable
    configure terminal
    interface e0/2
    no switchport
    ip address 192.167.XX.4 255.255.255.0
    no shutdown
    do write

Para que exista la comunicación hay que establecer las rutas estáticas entre J1 y J2 y ESW1.

La sede Central quedaría así:

![Alt text](img/Captura%20de%20pantalla%202023-04-25%20105855.png)

De nuevo se tuvo que agregar un switch, esta vez entre C3 y C1 y C2, las ips definidas anteriormente siguen siendo las mismas y la ip para la interfaz e0/1 de C3 quedaría definida como 192.177.XX.4, esta red también con máscara /24.

Se deben establecer las rutas estáticas necesarias para que existe la comunicación.