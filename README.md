# Bonfire-Rinkeby
The Bonfire Rinkeby contract is an example of the Bonfire mainnet contracts, where users gather together to burn ETH to make the existing ETH more rare. The Bonfire Rinkeby contract allows users try the Bonfire model without using real ETH. Visit a Rinkeby faucet to get your free funds. Visit the site here: [https://bonfireeth.github.io/Bonfire-Rinkeby/](https://bonfireeth.github.io/Bonfire-Rinkeby/)


## How it Works
1. At the beginning of each round, a hash containing a secret number (gathered randomly off-chain by the Bonfire chairs) to be used later as a salt for the random numbers, is set.

   The price of a seat/ticket for the bonfire is set. The price of the seats is adjusted before the first seat is taken. Once the first seat is sold the price can no longer be adjusted.
   
2. Users buy seats at the upcomming bonfire. The contract will not move forward until all of the seats have been sold.

3. Once all of the seats have been bought, random numbers are gather using Oraclize and their authenticity proofs.

4. After all of the random numbers from Oraclize have been gathered, the precommitted hash is revealed along with the secret number supplied by the Bonfire chairs. 

   The secret number is then used as a salt and combined with the each of random numbers (separately) to find which seats to give awards to. 40% of the ETH contributed is for awardees. The awardees can withdraw their awards from the contract on their own accord.
   
5. To end the round, 55% of the ETH contributed is burned. 5% of the ETH contributed is spread among the Bonfire chairs.   
   **burn wallet**: *0x0000000000000000000000000000000000000000*.  
   
   
## Command-line
Users can interact with the Bonfire contracts through geth (or MetaMask, Mist, etc.). Below are the contract address, contract abi, and the precommit/reveal hash events and awardees events to watch.

### Contract Address
*0x7f587a142390b5f2aad6b04a7e61ccd46e215794*

### Contract ABI
> [{"constant":true,"inputs":[],"name":"precommitHash","outputs":[{"name":"","type":"bytes32"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[],"name":"withdraw","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"banner","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"ticketCounter","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"owner","outputs":[{"name":"","type":"address"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"price","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[{"name":"","type":"address"}],"name":"awardeeMapping","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"message","type":"string"}],"name":"editBanner","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"saltNum","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[],"name":"withdraw","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"inputs":[],"payable":false,"stateMutability":"nonpayable","type":"constructor"},{"payable":true,"stateMutability":"payable","type":"fallback"},{"anonymous":false,"inputs":[{"indexed":false,"name":"txt","type":"string"}],"name":"BannerUpdated","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"txt","type":"string"},{"indexed":false,"name":"secretHash","type":"bytes32"}],"name":"SecretHashSet","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"value","type":"uint256"}],"name":"PriceUpdated","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"seatsLeft","type":"uint256"}],"name":"PledgeMade","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"secretHash","type":"bytes32"},{"indexed":false,"name":"textOne","type":"string"},{"indexed":false,"name":"secretNum","type":"uint256"},{"indexed":false,"name":"textTwo","type":"string"}],"name":"SecretHashRevealed","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"awardee","type":"address"},{"indexed":false,"name":"amount","type":"uint256"}],"name":"AwardeeSelected","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"burned","type":"uint256"}],"name":"BonfireCoinBurn","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"withdrawTo","type":"address"},{"indexed":false,"name":"withdrawAmount","type":"uint256"}],"name":"Withdrawal","type":"event"}]


### Precommit Hash Event
*var foo = contractName.SecretHashSet({}, {fromBlock: 0, toBlock: 'latest'});*

*foo.watch(function(error, result){console.log(results.args.txt + " " + result.args.secretHash)});*

### Reveal Hash Event
*var foo = contractName.SecretHashRevealed({}, {fromBlock: 0, toBlock: 'latest'});*

*foo.watch(function(error, result){console.log(result.args.secretHash + " " + result.args.textOne + " " + result.args.secretNum + " " + result.args.textTwo)});*

### Award Event
*var foo = contractName.AwardeeSelected({}, {fromBlock: 0, toBlock: 'latest'});*

*foo.watch(function(error, result){console.log(result.args.awardee + " " + result.args.amount)});*


## More Information
* A selfdestruct call burns **all** ETH held in the contract with **no** reward going to the Bonfire chair holders.

* One awardee receives 30% of the ETH contributed. All other awardees split 10% of the ETH contributed. Please buy seats responsibly.

* Feel free to download the files and run the site locally. But be sure to double check the contract address.

* Try Bonfire Rinkeby at: [https://bonfireeth.github.io/Bonfire-Rinkeby/](https://bonfireeth.github.io/Bonfire-Rinkeby/)

* Try Bonfire 15 - I at: [https://bonfireeth.github.io/Bonfire-15-I/](https://bonfireeth.github.io/Bonfire-15-I/)

* Try Bonfire 15 - V at: [https://bonfireeth.github.io/Bonfire-15-V/](https://bonfireeth.github.io/Bonfire-15-V/)

* Try Bonfire 150 - I at: [https://bonfireeth.github.io/Bonfire-150-I/](https://bonfireeth.github.io/Bonfire-150-I/)

* Try Bonfire 150 - V at: [https://bonfireeth.github.io/Bonfire-150-V/](https://bonfireeth.github.io/Bonfire-150-V/)

* Try Bonfire 250 - I at: [https://bonfireeth.github.io/Bonfire-250-I/](https://bonfireeth.github.io/Bonfire-250-I/)

* Try Bonfire 250 - V at: [https://bonfireeth.github.io/Bonfire-250-V/](https://bonfireeth.github.io/Bonfire-250-V/)
