-include .env

.PHONY: update anvil deploy test test-zksync

deploy-sepolia:
	forge script script/DeployFundMe.s.sol:DeployFundMe --rpc-url $(SEPOLIA_RPC_URL) --account Test01 --password test --broadcast --verify --etherscan-api-key $(ETHERSCAN_API_KEY) -vvvv

all: clean remove install update build

clean :; forge clean 

remove :; rm -rf .gitmodules && rm -rf .git/modules/* && rm -rf lib && touch .gitmodules && git add . && git commit -m "modules"

install :; forge install

update:; forge update

build :; forge build

anvil:;  anvil -m 'test test test test test test test test test test test junk' --steps-tracing --block-time 1

deploy:; forge script script/DeployStuff.s.sol:DeployStuff --broadcast --rpc-url http://localhost:8545  --account Test01 --password test   -vvvv 

interact:; forge script script/InteractWithStuff.s.sol:InteractWithStuff --broadcast --rpc-url http://localhost:8545  --private-key $(DEFAULT_ANVIL_KEY)   -vvvv 

zktest :; foundryup-zksync && forge test --zksync && foundryup

test :; forge test