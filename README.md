# PALABRAS RESERVADAS EN SOLIDITY *"KEYWORDS"*
Descripción de las palabras reservadas en Solidity, viendo sus usos en cada caso. 
Dentro de las palabras reservadas podemos encontrar **VARIABLES GLOBALES** , **MODIFICADORES** Y **PALABRAS RESERVADAS**
En caso de querer profundizar más, consultar la guía oficial https://solidity-es.readthedocs.io/es/latest/.

### DESCRIPCIÓN Y USO 
El funcionamento de este repositorio es en primera instancia la palabra , seguido de la descripción de la misma, y luego un ejemplo de código para poder ver más claro.

 ## Modificadores/ modifiers
 
### pure  (funciones)
Palabra reservada para funciones,  pure nos dice que no solo no guarda datos dentro de la blockchain , sino que tampoco lee datos de la blockchain.

```solidity
//promete ni leer ni modificar datos

  function add(uint i, uint j) public pure returns (uint) {
        return i + j;
    }
```
### view (funciones)
Muy parecidad al modificador pure, en el caso de view , si que puede visualizar el estado de la blockchain , pero en ningún caso modificarla, las diferencias con "pure" es básicamente el hecho de que se puede visualizar

```solidity
//promete ni leer ni modificar datos
  function add(uint i, uint j) public view returns (uint) {
        return i + j;
    }
```
### payable ( funciones) 

Palabra reservada que deja enviar Ether en la llamada, en caso de no tenerlo , no hay manera de hacer envíos de moneda de ningún tipo.
```solidity
    function deposit() public payable {}
```

### virtual y override (funciones y modificadores) 
En este caso las trato de manera conjunta ya que , una depende de la otra.
La palabra **virtual** se pone en funciones , y el funcionamiento que tiene es que en el de que esta función se pueda sobreescribir en el futuro, básicamente un contrate que herede de una función virtual
si tiene la palabra reservada **override** se podra sobreescribir.

```solidity

// el primer contrato tiene una función que en el caso del segundo contrato se hereda y se puede sobreescribir
contract Droid {
    function speak() public virtual returns (string memory) {
        return "Common droid tongue";
    }
}

contract R2D2 is Droid {
    function speak() public  override returns (string memory) {
        return "Beep boop beep";
    }
}
```
### constant (variables)
Las constantes son variables que no se pueden modificar.
En caso de tener una variable que no cambia de valor , es altamente recomendable usar constant , por el simple hecho de ahorrar Gas.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Constants {
    // Siempre usando mayúsculas , siguiendo la regla
    address public constant MY_ADDRESS = 0x777788889999AaAAbBbbCcccddDdeeeEfFFfCcCc;
}
```
### immutable (variables)
Una variable inmutable es una variable que apunta a un objeto y el valor del objeto no se puede cambiar, pero la variable se puede reasignar para que apunte a un nuevo objeto.
Los inmutables son diferentes de las variables constantes, que deben tener un valor fijo en el momento de la compilación y deben asignarse donde se declara la variable. Las variables constantes no pueden acceder al almacenamiento o a los datos de blockchain, mientras que las variables inmutables sí pueden.
Los inmutables se pueden utilizar para ahorrar costos de almacenamiento, ya que no requieren espacio de almacenamiento adicional para sus valores. Esto los hace útiles para almacenar valores como direcciones, hashes y otros datos que no necesitan cambiar con el tiempo. Además, los inmutables pueden ayudar a mejorar la legibilidad del código al facilitar la identificación de qué valores deben permanecer sin cambios durante la vigencia de un contrato.

 ```solidity
pragma solidity ^0.8.17;

contract MyContract {
    immutable uint public myNumber;

// reasignable en el constructor

    constructor(uint _myNumber) {
        myNumber = _myNumber;
    }
}
```

### anonymous (Eventos)
Para saber cómo tratar la keyword anonymous , hay que tener el cuenta que son los eventos, los eventos són básicamente logs para tener controlado eventos que pasan dentro de la blockchain, por ejemplo, que una address ha hecho una compra de más de 1 ethereum.
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract PaymentContract {
    event PaymentReceived(address indexed sender, uint256 amount);

    receive() external payable {
        require(msg.value >= 1 ether, "You must send 1 ether");
        emit PaymentReceived(msg.sender, msg.value);
        
        // Additional logic you might want to perform when receiving 1 ether.
    }
}
```
En este ejemplo se puede ver un evento que se ejecuta siempre que el usuario envíe un Ether o más.
