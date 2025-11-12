# nearx_smart_contracts_security

Repositório de validação de vulnerabilidades da disciplina de Segurança em Smart Contracts da NearX

Para esse exercício foi utilizado o código [Mapping](https://capturetheether.com/challenges/math/mapping/) do site [Capture the Ether](https://capturetheether.com/)

```solidity
pragma solidity ^0.4.21;

contract MappingChallenge {
    bool public isComplete;
    uint256[] map;

    function set(uint256 key, uint256 value) public {
        // Expand dynamic array as needed
        if (map.length <= key) {
            map.length = key + 1;
        }

        map[key] = value;
    }

    function get(uint256 key) public view returns (uint256) {
        return map[key];
    }
}

```

## Vulnerabilidades

1. **isComplete** público e sem utilização
2. Possibilidade de definição de valores e index que extrapolem o tamanho de dados, como por exemplo um comportamento inesperado ao se passar o valor maior que **uint256**
3. Não existe uma validação de valores, nem de quem pode fazer as ações
