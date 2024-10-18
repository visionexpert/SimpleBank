El contrato SimpleBank es un contrato inteligente escrito en Solidity que permite la gestión de un banco sencillo en la blockchain de Ethereum. Este contrato permite a los usuarios registrarse, depositar y retirar ETH (Ether), y también permite al propietario del contrato retirar fondos de la tesorería.

El contrato define una estructura User que almacena la información del usuario, incluyendo su nombre, apellido, balance y un indicador de si está registrado. Utiliza un mapping para relacionar las direcciones de los usuarios con su información correspondiente. Además, el contrato almacena la dirección del propietario (owner), la dirección de la tesorería (treasury), el fee en puntos básicos (fee), y el balance acumulado en la tesorería (treasuryBalance).

El contrato incluye varios eventos para registrar acciones importantes, como el registro de un usuario, la realización de un depósito, la realización de un retiro y el retiro de fondos de la tesorería por parte del propietario. También define modificadores para verificar si un usuario está registrado (onlyRegistered) y si el llamador es el propietario (onlyOwner).

El constructor del contrato inicializa el fee, la dirección de la tesorería y establece al propietario del contrato como la dirección que despliega el contrato. La función register permite a los usuarios registrarse proporcionando su nombre y apellido. La función deposit permite a los usuarios registrados depositar ETH en su cuenta. La función getBalance permite a los usuarios registrados verificar su saldo.

La función withdraw permite a los usuarios registrados retirar ETH de su cuenta, aplicando un fee que se transfiere a la tesorería. Finalmente, la función withdrawTreasury permite al propietario retirar fondos de la tesorería, asegurando que los fondos sean suficientes antes de realizar la transferencia.

En resumen, el contrato SimpleBank proporciona una implementación básica de un banco en la blockchain de Ethereum, permitiendo la gestión de registros de usuarios, depósitos y retiros de ETH, y la administración de una tesorería por parte del propietario del contrato.


   
      
     
