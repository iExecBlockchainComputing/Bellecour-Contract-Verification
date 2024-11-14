# BlockScout Smart Contract Verification Tool

A Go-based utility designed to automate the verification of Ethereum smart contracts on BlockScout, specifically tailored for the Bellecour network. This tool helps in fetching verified contracts, transforming their compiler settings, and re-verifying them on a newer instance of BlockScout.

Table of Contents

	•	Features
	•	Installation
	•	Usage
	•	1. Fetch Verified Smart Contracts
	•	2. Transform JSON and Verify
	•	Configuration

## Features

	•	Automatically fetch verified contracts from BlockScout (Bellecour V5).
	•	Transform compiler settings into a standard JSON format compatible with BlockScout V6.
	•	Submit contracts for re-verification on Bellecour BlockScout V6.
	•	Comprehensive error handling and logging to track the verification status.

## Installation

To run this tool, you need to have Go installed. Follow these steps to set it up:

1.	Clone the Repository:

```
git clone https://github.com/yourusername/blockscout-smart-contract-verification-tool.git
cd blockscout-smart-contract-verification-tool
``` 


2.	Install Dependencies:
The script uses the Go standard library only. If there are external dependencies, run:
```
go mod tidy
```


3.	Build the Application:
```
go build
```

## Usage

1. Fetch Verified Smart Contracts

The tool can query all verified contracts from the Bellecour BlockScout V5 API.

Run the following command to fetch verified contract addresses:
```
go run main.go
```

This command will generate a list of verified contract addresses from BlockScout V5.

2. Transform JSON and Verify

The fetched contract data is transformed into a standard JSON format and then submitted for verification on BlockScout V6.

Example usage to verify a single contract:

QuerySmartContractVerify("0xYourSmartContractAddressHere")

You can modify the main() function to verify multiple contracts:
```go
listOfContractAddresses := []string{
    "0xAddress1",
    "0xAddress2",
}
for _, smartContractAddress := range listOfContractAddresses {
    QuerySmartContractVerify(smartContractAddress)
}
```

The verified contracts will be available on Bellecour BlockScout V6 with a direct link printed in the console.

### Configuration

This tool uses a few key API endpoints:

	•	BlockScout V5: To query the verified contracts.
	•	Endpoint: https://blockscout-v5.bellecour.iex.ec/api
	•	BlockScout V6: To verify contracts.
	•	Endpoint: https://blockscout.bellecour.iex.ec/api/v2/smart-contracts/

Ensure you replace the url variable in QuerySmartContractVerify() with the correct endpoint if you’re using a different network or explorer instance.

### Parameters:

	•	address_hash: The contract address to be verified.
	•	compiler_version: The version of the Solidity compiler used.
	•	contract_name: The name of the contract.
	•	files: The transformed contract settings JSON (standard input format).
