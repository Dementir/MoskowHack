#  Task 4: Lottery

## @About
Fancy entrepreneur Stanislav Navrody decided to found his new blockchain startup - a lottery for the pensioners. From previous experience you don't trust him too much, prove that is not a such a good idea.

## @Task
Your goal is to assign true to the "contract_status" variable

contract_status == true;


Your smart contract is at 0xaFdc58734a387D9dE7c6999629a7fa27e0312285 on Rinkeby network

```javascript
contract Lottery {

  address owner;

  address[1001] public participators;

  address public winner;

  uint256 sum;

  address public winContract;

  constructor () {

    owner = msg.sender;
    participators[1] = 0xca35b7d915458ef540ade6068dfe2f44e8fa723c;
    participators[2] = 0xca35b7d915458ef540ade6068dfe2f44e8fa743c;
    //
    // ...
    participators[1000] = 0xca35b7d915458ef540ade6068dfe2f44e8fa343c;

  }

  modifier onlyOwner() {
    require(owner == msg.sender);
    _;
  }


  function participate() payable {
    require(msg.value >= 0.1 ether);
    participators[0] = msg.sender;
  }

  uint256 private pi = 31415926535897932384626433832795;

  function initLottery(uint256 _lot)  {
    require(_lot < pi - 1000);
    uint256 _winner = uint256((uint256(uint256(block.blockhash(block.number - 10)))
    / pi % 1000) + _lot) % 1000;
    setWinnerAddress(participators[_winner]);
  }

  function setWinnerAddress(address _target) {
    winner = _target;
  }

  function sendToWinner() {
    SuperContract s = SuperContract(winContract);
    s.setOwner(winner);
  }

  function setSuperContract(address _c) onlyOwner {
    winContract = _c;
  }

  function status() external view returns (bool) {
      SuperContract s = SuperContract(winContract);
      return s.status();
  }
}

contract SuperContract {

  address owner;

  bool private contract_status;

  constructor () {
    owner = msg.sender;
  }

  function status() external view returns (bool) {
    return contract_status;
  }

  function solved() private {
    contract_status = true;
  }

  modifier onlyOwner() {
    require(owner == msg.sender);
    _;
  }

  function setOwner(address _owner) onlyOwner {
    owner = _owner;
  }


  function withdraw() onlyOwner {}

  function win() onlyOwner {
    solved();
  }

}
```
