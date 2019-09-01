---
description: Contract is written in Vyper (0.1.0b9)
---

# Stablecoinswap API



## addLiquidity

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
def addLiquidity(
    token_address: address, 
    erc20_token_amount: uint256, 
    deadline: timestamp
) -> bool
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.addLiquidity(token_address, amount, deadline).send({ from: user_address }, callback)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| token\_address | address | Address of ERC20 token to add |
| erc20\_token\_amount | uint256 | How many ERC20 tokens to add |
| deadline | uint256 | Transaction deadline |

| Returns |  |
| :--- | ---: |
| bool | True if successful. Reverts or false on failure |

## removeLiquidity

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
def removeLiquidity(
    token_address: address, 
    stableswap_token_amount: uint256, 
    erc20_min_output_amount: uint256, 
    deadline: timestamp
) -> bool
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```
 contract.methods.removeLiquidity(token_address, amount, min_output_amount, deadline).send({ from: user_address }, callback)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| token\_address | address | Address of ERC20 token to remove |
| stableswap\_token\_amount | uint256 | Amount of STL tokens to redeem |
| erc20\_min\_output\_amount | uint256 | Minimum ERC20 tokens output amount |
| deadline | uint256 | Transaction deadline |

| Returns |  |
| :--- | ---: |
| bool | True if successful. Reverts or false on failure |

## swapTokens

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
def swapTokens(
    input_token: address,
    output_token: address, 
    erc20_input_amount: uint256, 
    erc20_min_output_amount: uint256, 
    deadline: timestamp
) -> bool
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```
contract.methods.swapTokens(input_token_address, output_token_address, input_amount, min_output_amount, deadline).send({ from: this.currentAddress() }, callback)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| input\_token | address | Address of input  ERC20 token |
| output\_token | address | Address of output ERC20 token |
| erc20\_input\_amount | uint256 | Amount of ERC20 input tokens sold |
| erc20\_min\_output\_amount | uint256 | Minimum ERC20 output tokens to buy |
| deadline | uint256 | Transaction deadline |

| Returns |  |
| :--- | ---: |
| bool | True if successful. Reverts or false on failure |

## tokenExchangeRateAfterFees

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
@constant
def tokenExchangeRateAfterFees(
    input_token_address: address, 
    output_token_address: address
) -> uint256
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.tokenExchangeRateAfterFees(input_token_address, output_token_address).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| input\_token\_address | address | Address of ERC20 token to sell |
| output\_token\_address | address | Address of ERC20 token to buy |

<table>
  <thead>
    <tr>
      <th style="text-align:left">Returns</th>
      <th style="text-align:right"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">uint265</td>
      <td style="text-align:right">
        <p>Exchange rate is given at the base level of precision (it is multiplied
          by 10^(output_token.decimals - input_token.decimals + 22)).</p>
        <p>Note that due to rounding, the fees could be slightly higher for the tokens
          with smaller decimal precision and/or if the exchange amount is too low.</p>
      </td>
    </tr>
  </tbody>
</table>## tokenOutputAmountAfterFees

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
@constant
def tokenOutputAmountAfterFees(
    input_token_amount: uint256, 
    input_token_address: address, 
    output_token_address: address
) -> uint256
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.tokenOutputAmountAfterFees(amount, input_token_address, output_token_address).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| input\_token\_amount | uint256 | Amount of ERC20 token to sell |
| input\_token\_address | address | Address of ERC20 token to sell |
| output\_token\_address | address | Address of ERC20 token to buy |

| Returns |  |
| :--- | ---: |
| uint256 | How many tokens can be bought for a given amount of input tokens |

## poolOwnership

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
@constant
def poolOwnership(user_address: address) -> decimal
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.poolOwnership(address).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| user\_address | address | Address of a user |

| Returns |  |
| :--- | ---: |
| fixed168x10 \(uint168\) | Share of total liquidity belonging to the user |

## fees

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
@constant
def fees(fee_name: string[32]) -> decimal
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.fees(fee_name).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| fee\_name | string | 'ownerFee' or 'tradeFee' |

| Returns |  |
| :--- | ---: |
| fixed168x10 \(uint168\) | Fee value \(i.e. 0.001 means 0.1%\) |

## inputTokens

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
inputTokens: public(map(address, bool))
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.inputTokens(address).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| address | address | Address of ERC20 token |

| Returns |  |
| :--- | ---: |
| bool | True if an address is in the list of available input tokens |

## outputTokens

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
outputTokens: public(map(address, bool))
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.outputTokens(address).call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| address | address | Address of ERC20 token |

| Returns |  |
| :--- | ---: |
| bool | True if an address is in the list of available output tokens |

## priceOracleAddress

{% code-tabs %}
{% code-tabs-item title="Smart Contract" %}
```python
priceOracleAddress: public(address)
```
{% endcode-tabs-item %}

{% code-tabs-item title="Web3" %}
```javascript
contract.methods.priceOracleAddress().call()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

| Returns |  |
| :--- | ---: |
| address | Address of a priceoracle contract |

