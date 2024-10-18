El contrato SimpleBank es un contrato inteligente escrito en Solidity que permite la gestión de un banco sencillo en la blockchain de Ethereum. Este contrato permite a los usuarios registrarse, depositar y retirar ETH (Ether), así como verificar su saldo. Además, el propietario del contrato tiene la capacidad de retirar fondos de la tesorería del banco.

El contrato define una estructura User que almacena la información del usuario, incluyendo su nombre, apellido, balance y un indicador de si está registrado. Esta información se almacena en un mapping que relaciona las direcciones de los usuarios con sus datos.

El contrato también define varias variables de estado importantes: owner (la dirección del propietario del contrato), treasury (la dirección de la tesorería), fee (la tarifa en puntos básicos) y treasuryBalance (el balance acumulado en la tesorería en wei).

Se definen varios eventos para notificar sobre acciones importantes, como el registro de un usuario, la realización de un depósito, un retiro y el retiro de fondos de la tesorería por parte del propietario.

El contrato incluye varios modificadores para verificar condiciones específicas: onlyRegistered asegura que solo los usuarios registrados puedan ejecutar ciertas funciones, y onlyOwner asegura que solo el propietario del contrato pueda ejecutar otras funciones.

El constructor del contrato inicializa las variables de estado fee y treasury, y establece al creador del contrato como el propietario.

El contrato proporciona varias funciones clave:

register: permite a los usuarios registrarse proporcionando su nombre y apellido.
deposit: permite a los usuarios registrados depositar ETH en su cuenta.
getBalance: permite a los usuarios registrados verificar su saldo.
withdraw: permite a los usuarios registrados retirar ETH de su cuenta, aplicando una tarifa.
withdrawTreasury: permite al propietario retirar fondos de la tesorería.
En resumen, SimpleBank es un contrato inteligente que facilita la gestión de un banco sencillo en la blockchain, permitiendo a los usuarios realizar operaciones básicas con ETH y proporcionando mecanismos de seguridad y notificación a través de eventos y modificadores.



