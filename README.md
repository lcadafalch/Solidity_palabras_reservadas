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

### virtual (funciones y modificadores) y override
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
