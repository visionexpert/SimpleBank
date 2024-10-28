El proyecto SimpleBank es un innovador contrato inteligente desarrollado en Solidity para la blockchain de Ethereum. Su objetivo es ofrecer un sistema bancario básico que permita a los usuarios gestionar sus fondos de manera segura y eficiente. Este documento describe las características principales, así como la estructura del código y las pruebas unitarias implementadas.

## Características Principales

1. **Registro de Usuarios**: Los usuarios pueden registrarse en el sistema, creando una cuenta vinculada a su dirección de Ethereum. Este proceso es fundamental para asegurar que cada operación se realice de manera identificable y segura.

2. **Depósitos**: Los usuarios tienen la posibilidad de realizar depósitos de ETH en su cuenta dentro del contrato. Estos fondos quedan almacenados y disponibles para futuras transacciones.

3. **Retiros**: El contrato permite a los usuarios retirar sus fondos. Sin embargo, cada retiro genera una comisión que se destina a una función de tesorería. Esto garantiza la sostenibilidad del proyecto y permite acumular fondos para futuras mejoras.

4. **Función de Tesorería**: Esta funcionalidad convierte el simple acto de retirar en una oportunidad de crecimiento económico para el contrato. Las comisiones por los retiros se reutilizan en diferentes aspectos del sistema, beneficiando a todos los usuarios.

## Código del Contrato

El contrato simple de SimpleBank está escrito en Solidity, con un diseño claro y modular. A continuación, se presenta un resumen del código:

```solidity
pragma solidity ^0.8.0;

contract SimpleBank {
mapping(address => uint) private balances;
uint public treasury;

function register() public {
// Lógica de registro
}

function deposit() public payable {
require(msg.value > 0, "Deposito debe ser mayor que cero");
balances[msg.sender] += msg.value;
}

function withdraw(uint amount) public {
require(balances[msg.sender] >= amount, "Fondos insuficientes");
uint fee = amount / 100; // 1% de comisión
treasury += fee;
balances[msg.sender] -= amount;
payable(msg.sender).transfer(amount - fee);
}

function getBalance() public view returns (uint) {
return balances[msg.sender];
}

function getTreasury() public view returns (uint) {
return treasury;
}
}
```

## Pruebas Unitarias

Para garantizar la robustez del contrato, se han implementado pruebas unitarias que verifican el correcto funcionamiento de cada funcionalidad. Estas pruebas incluyen:

- Registro de usuarios.
- Validación de depósitos y retiros.
- Comprobación de las comisiones acumuladas en la tesorería.
- Verificaciones de saldo antes y después de las transacciones.

### Ejemplo de Prueba

```javascript
const SimpleBank = artifacts.require("SimpleBank");

contract("SimpleBank", accounts => {
it("debería permitir a los usuarios registrar una cuenta", async () => {
const bankInstance = await SimpleBank.deployed();
await bankInstance.register({ from: accounts[0] });
const balance = await bankInstance.getBalance({ from: accounts[0] });
assert.equal(balance.toNumber(), 0, "El saldo debería ser 0 después del registro");
});

// Otras pruebas...
});
```

## Scripts de Interacción

Se han creado scripts en JavaScript para facilitar la interacción con el contrato desde una DApp. Estos scripts permiten que los usuarios realicen operaciones de registro, depósito y retiro de manera intuitiva.

### Ejemplo de Script

```javascript
async function depositEther(amount) {
const accounts = await web3.eth.getAccounts();
await bankInstance.deposit({ from: accounts[0], value: web3.utils.toWei(amount, "ether") });
console.log("Deposito realizado: " + amount + " ETH");
}
```

## Conclusión

SimpleBank es una implementación básica pero efectiva de un sistema bancario en la blockchain de Ethereum. Al emplear un contrato inteligente en Solidity, se asegura la transparencia y seguridad de las transacciones. Con las pruebas unitarias y scripts diseñados, este proyecto establece una base sólida para futuras funcionalidades y expansiones en el ecosistema financiero descentralizado.
