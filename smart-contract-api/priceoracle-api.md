---
description: Contract is written in Vyper (0.1.0b9)
---

# Priceoracle API

## poolSize

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
@constant
def poolSize(contract_address: address) -> uint256
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.poolSize(stablecoinswap_address).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| contract\_address | address | Address of a stablecoinswap contract |

| Returns |  |
| :--- | ---: |
| uint256 | Total pool size of stablecoinswap contract in USD multiplied by 10\*\*18 |

## supported\_tokens

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
supported_tokens: public(address[5])
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```
contract.methods.supported_tokens(index).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| index | uint | Index of a supported token \(0 to 4\) |

| Returns |  |
| :--- | ---: |
| address | Address of ERC20 token |

## normalized\_token\_prices

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
normalized_token_prices: public(map(address, uint256))
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.normalized_token_prices(token_address).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| address | address | Address of ERC20 token contract |

| Returns |  |
| :--- | ---: |
| uint256 | Returns normalized price in USD for a token at given address.  |

Where:

`normalized_usd_price = usd_price * 10**8 * 10**(18 - token.decimals)`

Example: USD price for USDC = $0.97734655, token has 6 decimals:

`normalized_usd_price = 97734655000000000000`

