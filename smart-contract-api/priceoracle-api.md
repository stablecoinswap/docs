---
description: Contract is written in Vyper (0.1.0b9)
---

# Priceoracle API

## poolSize

{% tabs %}
{% tab title="Smart Contract" %}
```python
@constant
def poolSize(contract_address: address) -> uint256
```
{% endtab %}

{% tab title="Web3" %}
```javascript
contract.methods.poolSize(stablecoinswap_address).call()
```
{% endtab %}
{% endtabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| contract\_address | address | Address of a stablecoinswap contract |

| Returns |  |
| :--- | ---: |
| uint256 | Total pool size of stablecoinswap contract in USD multiplied by 10\*\*18 |

## supportedTokens

{% tabs %}
{% tab title="Smart Contract" %}
```python
supportedTokens: public(address[5])
```
{% endtab %}

{% tab title="Web3" %}
```
contract.methods.supported_tokens(index).call()
```
{% endtab %}
{% endtabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| index | uint | Index of a supported token \(0 to 4\) |

| Returns |  |
| :--- | ---: |
| address | Address of ERC20 token |

## normalized\_token\_prices

{% tabs %}
{% tab title="Smart Contract" %}
```python
normalized_token_prices: public(map(address, uint256))
```
{% endtab %}

{% tab title="Web3" %}
```javascript
contract.methods.normalized_token_prices(token_address).call()
```
{% endtab %}
{% endtabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| address | address | Address of ERC20 token contract |

| Returns |  |
| :--- | ---: |
| uint256 | Returns normalized price in USD for a token at given address.  |

Where:

`normalized_usd_price = usd_price * 10**8 * 10**(18 - token.decimals)`

Example: USD price for USDC = $1.0, token has 6 decimals:

`normalized_usd_price = 100000000000000000000`

USD price for DAI token is the price according to [https://etherscan.io/address/0x787f552bdc17332c98aa360748884513e3cb401a](https://etherscan.io/address/0x787f552bdc17332c98aa360748884513e3cb401a#readContract) and USD price for any other token is always $1.0

