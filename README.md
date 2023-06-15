# caliper-workspace
Caliper configuration of the feasibility project example is provided for the community

1. Ubuntu and WSL2 is used under Windows. Mac and Linux (Ubuntu/Debian based distro) is also supported.
2. It is assumed the latest Hyperledger Fabric is installed. Follow the instructions at https://hyperledger-fabric.readthedocs.io/en/latest/install.html
3. Download the Caliper configuration files provided here. Directory caliper-workspace should be at the same level as the fabric-samples.
4. Navigate to fabric-samples/test-network
5. Start the network and install asset-transfer basic chaincode with the following commands.
./network.sh up createChannel
./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go -ccl go
6. Navigate to caliper-workspace
7. Unzip node_modules.7z (optional, install command downloads it from scratch).
8. Install and bind Caliper with the following commands. If node_modules.7z was unzipped, install will retrieve any updated files.
npm install --only=prod @hyperledger/caliper-cli@0.5.0
npx caliper bind --caliper-bind-sut fabric:2.2
9. Run a test with the following command. Network and benchmark configuration file names are provided. Modify benchmark configuration file as needed.
npx caliper launch manager --caliper-workspace ./ --caliper-networkconfig networks/networkconfig.yaml --caliper-benchconfig benchmarks/benchconfig.yaml --caliper-flow-only-test
10. A report is printed and a report.html file produced in caliper-workspace directory.
11. Modify benchmark configuration file as needed in order to repeat the test.
