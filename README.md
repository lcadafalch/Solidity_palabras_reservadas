# PALABRAS RESERVADAS EN SOLIDITY *"KEYWORDS"*
Descripción de las palabras reservadas en Solidity, viendo sus usos en cada caso. 
Dentro de las palabras reservadas podemos encontrar **VARIABLES GLOBALES** , **MODIFICADORES** Y **PALABRAS RESERVADAS**
En caso de querer profundizar más, consultar la guía oficial https://solidity-es.readthedocs.io/es/latest/.

### DESCRIPCIÓN Y USO 
El funcionamento de este repositorio es en primera instancia la palabra , seguido de la descripción de la misma, y luego un ejemplo de código para poder ver más claro.

 ## Modificadores/ modifiers
 
### pure  
Palabra reservada para funciones,  pure nos dice que no solo no guarda datos dentro de la blockchain , sino que tampoco lee datos de la blockchain.

```solidity
//promete ni leer ni modificar datos

  function add(uint i, uint j) public pure returns (uint) {
        return i + j;
    }
```
### view 
Muy parecidad al modificador pure, en el caso de view , si que puede visualizar el estado de la blockchain , pero en ningún caso modificarla, las diferencias con "pure" es básicamente el hecho de que se puede visualizar

//promete ni leer ni modificar datos

  function add(uint i, uint j) public view returns (uint) {
        return i + j;
    }
```

