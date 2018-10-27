# Task 2: BrokenVisaCard

## @About
Young solidity developer just deployed smart contract but has forgotten to make a really important function to be payable. Right now he shows the demo on the investor and wants to pay to the contact in any way. Can you help him?

## @Task
Your goal is to assign true to the "contract_status" variable

contract_status == true;


Your smart contract is at ---- on Rinkeby network

```javascript
contract BrokenVisaCard {

  constructor () {
    totalRealEthAmount = - (10 * 17);
  }

  int256 totalRealEthAmount;

  mapping(address => int256) ethBalanceOfPerson;

  bool private contract_status;

  function solved() private {
    contract_status = true;
  }

  function Debit(address _pay, uint256 _sum) {
    require(ethBalanceOfPerson[msg.sender] >= int256(_sum));
    _pay.transfer(_sum);
  }

  function Credit(uint256 sum) {
    ethBalanceOfPerson[msg.sender] -= int256(sum);
    msg.sender.transfer(sum);
  }

  function status() public view returns (bool) {
    return contract_status;
  }

  // somebody forget to make it payable
  function payForDebts() {
    ethBalanceOfPerson[msg.sender] += int256(msg.value);
    // totalRealEthAmount += msg.value - somebody commented that
    if (address(this).balance >= 0) {
      solved();
    }
  }

  function() payable {
    throw;
  }
}

```
