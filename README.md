# Poly-proof-module-3

**Aim of the project**

 Implement the circuit using circom programming language and deploy a verifier on-chain to verify proofs generated from this circuit.

**Code of the program**

     pragma circom 2.0.0;

     template MyCustomCircuit () 
     
     { 
     
      //signal inputs
      
      signal input a;
      signal input b;

      //signals from gates
      signal x;
      signal y;

      //final signal output
      signal output q;

      //component gates used to create custom circuit
      component andGate = AND();
      component notGate = NOT();
      component orGate = OR();


      //circuit logic
      andGate.a<==a;
      andGate.b<==b;
      x<==andGate.out;

      notGate.in<==b;
      y<==notGate.out;

     orGate.a<==x;
     orGate.b<==y;
     q<==orGate.out;

      }
    template AND() {
    
    signal input a;
    signal input b;
    signal output out;

    out <== a*b;
    }

    template NOT() {
      signal input in;
      signal output out;

      out <== 1 + in - 2*in;
      
    }

    template OR() {
   
      signal input a;
      signal input b;
      signal output out;

      out <== a + b - a*b;
    }
    
     component main = MyCustomCircuit();

**Logic of the code**

1. Declare a and b as the signal inputs and x and y as the signals from the gates.

2. Declare q to be the final output from the circuit.

3. Write the component gates(andGate, notGate, and orGate) which will be used while creating our customized circuit.

4. In the input.json file, initialize a=0 and b=1.

5. First of all, pass a and b as the inputs to the andGate. Here we are getting x as its output.(a=0,b=1,x=0)

6. Then we pass b as an input to notGate and hence receive y as its output.(b=1,y=0)

7. Additionally, pass x and y as inputs to the orGate and we receive q as a final output. (x=0,y=0,q=0)

8. Lastly we have the templates of our gates which will be implementing the logicality of our circuit.

**Functionality of the code**

1. Clone the repository provided in the module to gitpod.

2. Write the above-provided code in the circuit .circom file.

3. Open the terminal and type the command "npm i" to install the project dependencies.

4. Add the test network in our hardhat.config.ts file.

5. Paste the wallet address' private key in the .env file.

6. Then type "npx hardhat circom" in order to compile the circuit.

7. Lastly type "npx hardhat run scripts/deploy.ts" in order to deploy the verifier onto our test network.

8. Subsequently, open the polygonscan.com to confirm our transaction.

9. Paste the deployed contract address into the search bar and verify the trasaction as the status returns to be success.

10. Open the metamask wallet. There it shows the deducted amount from our wallet.

**Author**

Sehajpreet Kaur
(21BCS4518@cuchd.in)

