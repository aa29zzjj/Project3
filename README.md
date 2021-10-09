# 95-702 Distributed Systems For Information Systems Management
## Project 3 Fall 2021


Assigned: Friday, October 8, 2021
Due Friday, October 22, 11:59pm


### Principles
One of our primary objectives in this course is to make clear the fundamental
distinction between functional and nonfunctional characteristics of distributed
systems. The functional characteristics describe the business or organizational
purpose of the system. The non-functional characteristics affect the quality of
the system. Is it fast? Does it easily interoperate with others? Is it fault
tolerant? Is it reliable and secure?

In this project, we will illustrate an important nonfunctional characteristic
of blockchain technology - its tamper evident design. We will build a stand-alone
blockchain (Task 0) and a distributed system where a remote client interacts with a blockchain API (Task 1).

Note that this is not all of blockchain. There is more to learn. Real blockchains are decentralized and include peer to peer communication and many replicas of the blockchain. The blocks themselves typically include Merkle Trees. This
assignment does not do all of that but it does provide a foundation to build on.

### Overview

In Task 0, you will write a blockchain by carefully following the directions found [in this Javadoc](http://www.andrew.cmu.edu/course/95-702/examples/javadoc/index.html).

Note that the Javadoc describes writing "data" or a "transaction" to the blockchain. In this project, our "data" or "transaction" will be simple statements transferring "dscoin" from one player to another.

The Javadoc describes two classes that you need to write - Block.java and BlockChain.java.

In Task 1, you will distribute the application that you created in Task 0. You will write a client server application. The interaction between the client and the server will be with JSON messages over TCP sockets. Thus, your work from Project2 will be very useful and may be reused here.

You will be submitting complete Java programs and screenshots on a single PDF file. These should be clearly labelled as described below.

You will also be submitting two IntelliJ projects as two zip files.
See below for a precise description of what needs to be submitted.

Documenting code is important. Be sure to provide comments in your code explaining what the code is doing and why.

Be sure to separate concerns when appropriate.

Be sure to include comments within your methods.

Data validation (of user input) is very important but we are not doing that here.

Any code from external sources, e.g., stack overflow, **must be clearly cited with a URL**.

## Task 0  

Write a solution to Task 0 by studying the Javadoc provided (Block.java and BlockChain.java). The logic found in Task 0 will be reused in Task 1.

The execution of Task 0, a non-distributed stand-alone program, will look like the following interaction. As part of the submission of Task 0, you must turn in a screenshot similar to the one below.

Label this first section ***Task 0 Execution*** in your PDF. Of course, your code - not mine - will generate the screen shot.

In addition, wherever the name Alice is used, replace "Alice" with your name.

### Task 0 Execution

```
0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. corrupt the chain.
5. Hide the corruption by repairing the chain.
6. Exit
0
Current size of chain: 1
Difficulty of most recent block: 2
Total difficulty for all blocks: 2
Approximate hashes per second on this machine: 1233045
Expected total hashes required for the whole chain: 256.000000
Nonce for most recent block: 329
Chain hash: 00ED9CDD85C056D94B2DE633C0AE2929325C82166FF75FCB14ABF3C4B2A2B8FC

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
3
Enter transaction
Alice pays Bob 100 dscoin
Total execution time to add this block was 338 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
3
Enter transaction
Bob pays Alice 20 dscoin
Total execution time to add this block was 56 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
4
Enter transaction
Alice pays Carol 23 dscoin
Total execution time to add this block was 961 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
5
Enter transaction
Donna pays Alice 34 dscoin
Total execution time to add this block was 64471 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-10-08 18:15:10.722","Tx ": "Genesis","PrevHash" : "","nonce" : 329,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-10-08 18:23:17.467","Tx ": "Alice pays Bob 100 dscoin","PrevHash" : "00ED9CDD85C056D94B2DE633C0AE2929325C82166FF75FCB14ABF3C4B2A2B8FC","nonce" : 6392,"difficulty": 3},
{"index" : 2,"time stamp " : "2021-10-08 18:23:44.451","Tx ": "Bob pays Alice 20 dscoin","PrevHash" : "000F00F3C900866C6089FF4383CE9BECE87FF411A85B148CAF1FF7C008FAB4DD","nonce" : 1834,"difficulty": 3},
{"index" : 3,"time stamp " : "2021-10-08 18:24:12.823","Tx ": "Alice pays Carol 23 dscoin","PrevHash" : "0002233662260C8608C733A11F95B5130918248103BA65720AF0735E2DD74482","nonce" : 39388,"difficulty": 4},
{"index" : 4,"time stamp " : "2021-10-08 18:24:38.258","Tx ": "Donna pays Alice 34 dscoin","PrevHash" : "0000E9A85ADBF45FCE662E468E42677B0DA6CB987C27FA33A4161B915515FAFB","nonce" : 2720045,"difficulty": 5}
 ], "chainHash":"00000EF8806B50817A295CB700A370CEA76A538F83BF7278102CBE4EA309F8CD"}

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
2
Enter transaction
Carol pays Donna 1 dscoin
Total execution time to add this block was 5 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-10-08 18:15:10.722","Tx ": "Genesis","PrevHash" : "","nonce" : 329,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-10-08 18:23:17.467","Tx ": "Alice pays Bob 100 dscoin","PrevHash" : "00ED9CDD85C056D94B2DE633C0AE2929325C82166FF75FCB14ABF3C4B2A2B8FC","nonce" : 6392,"difficulty": 3},
{"index" : 2,"time stamp " : "2021-10-08 18:23:44.451","Tx ": "Bob pays Alice 20 dscoin","PrevHash" : "000F00F3C900866C6089FF4383CE9BECE87FF411A85B148CAF1FF7C008FAB4DD","nonce" : 1834,"difficulty": 3},
{"index" : 3,"time stamp " : "2021-10-08 18:24:12.823","Tx ": "Alice pays Carol 23 dscoin","PrevHash" : "0002233662260C8608C733A11F95B5130918248103BA65720AF0735E2DD74482","nonce" : 39388,"difficulty": 4},
{"index" : 4,"time stamp " : "2021-10-08 18:24:38.258","Tx ": "Donna pays Alice 34 dscoin","PrevHash" : "0000E9A85ADBF45FCE662E468E42677B0DA6CB987C27FA33A4161B915515FAFB","nonce" : 2720045,"difficulty": 5},
{"index" : 5,"time stamp " : "2021-10-08 18:26:27.032","Tx ": "Carol pays Donna 1 dscoin","PrevHash" : "00000EF8806B50817A295CB700A370CEA76A538F83BF7278102CBE4EA309F8CD","nonce" : 109,"difficulty": 2}
 ], "chainHash":"008FBEA31B846E68BF183237F5285F2EE739E26C22BFABDC4E9CB0EC184EE9C8"}

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
4
corrupt the Blockchain
Enter block ID of block to corrupt
0
Enter new data for block 0
Carol pays Alice 1000 dscoin
Block 0 now holds Carol pays Alice 1000 dscoin

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-10-08 18:15:10.722","Tx ": "Carol pays Alice 1000 dscoin","PrevHash" : "","nonce" : 329,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-10-08 18:23:17.467","Tx ": "Alice pays Bob 100 dscoin","PrevHash" : "00ED9CDD85C056D94B2DE633C0AE2929325C82166FF75FCB14ABF3C4B2A2B8FC","nonce" : 6392,"difficulty": 3},
{"index" : 2,"time stamp " : "2021-10-08 18:23:44.451","Tx ": "Bob pays Alice 20 dscoin","PrevHash" : "000F00F3C900866C6089FF4383CE9BECE87FF411A85B148CAF1FF7C008FAB4DD","nonce" : 1834,"difficulty": 3},
{"index" : 3,"time stamp " : "2021-10-08 18:24:12.823","Tx ": "Alice pays Carol 23 dscoin","PrevHash" : "0002233662260C8608C733A11F95B5130918248103BA65720AF0735E2DD74482","nonce" : 39388,"difficulty": 4},
{"index" : 4,"time stamp " : "2021-10-08 18:24:38.258","Tx ": "Donna pays Alice 34 dscoin","PrevHash" : "0000E9A85ADBF45FCE662E468E42677B0DA6CB987C27FA33A4161B915515FAFB","nonce" : 2720045,"difficulty": 5},
{"index" : 5,"time stamp " : "2021-10-08 18:26:27.032","Tx ": "Carol pays Donna 1 dscoin","PrevHash" : "00000EF8806B50817A295CB700A370CEA76A538F83BF7278102CBE4EA309F8CD","nonce" : 109,"difficulty": 2}
 ], "chainHash":"008FBEA31B846E68BF183237F5285F2EE739E26C22BFABDC4E9CB0EC184EE9C8"}

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
5
Repairing the entire chain
Total execution time required to repair the chain was 11159 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-10-08 18:15:10.722","Tx ": "Carol pays Alice 1000 dscoin","PrevHash" : "","nonce" : 43,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-10-08 18:23:17.467","Tx ": "Alice pays Bob 100 dscoin","PrevHash" : "00324633B5875FF14A67B3C933E13F9C86FBCB02C85A87C64A8415BD88A35DDF","nonce" : 1188,"difficulty": 3},
{"index" : 2,"time stamp " : "2021-10-08 18:23:44.451","Tx ": "Bob pays Alice 20 dscoin","PrevHash" : "0001FCEAFB46C7D82E081F3B0E35C78143227A2F76FC06F6400A9F1BBD514C65","nonce" : 4904,"difficulty": 3},
{"index" : 3,"time stamp " : "2021-10-08 18:24:12.823","Tx ": "Alice pays Carol 23 dscoin","PrevHash" : "000EE0549B03BD2DEFF7716074D916DD41D71F4179012A08CBC4C4E98D159839","nonce" : 74716,"difficulty": 4},
{"index" : 4,"time stamp " : "2021-10-08 18:24:38.258","Tx ": "Donna pays Alice 34 dscoin","PrevHash" : "0000D93803482E9D4D4CA450FD0F00F83382572039BF18FCF00471E3E2D23821","nonce" : 398036,"difficulty": 5},
{"index" : 5,"time stamp " : "2021-10-08 18:26:27.032","Tx ": "Carol pays Donna 1 dscoin","PrevHash" : "00000859EA2603CFFAB423DD4D057D1A183153C8D5D870370B381B9642DA9FDA","nonce" : 179,"difficulty": 2}
 ], "chainHash":"00591884CDD68FF5B8ABC5906541B192837288F7A28C630C2E730FC397D5BD7E"}

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
4
Enter transaction
Edward pays Alice 34 dscoin
Total execution time to add this block was 531 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
2
Verifying entire chain
Chain verification: true
Total execution time required to verify the chain was 2 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
4
corrupt the Blockchain
Enter block ID of block to corrupt
2
Enter new data for block 2
Frank pays Alice 3 dscoin
Block 2 now holds Frank pays Alice 3 dscoin

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
2
Verifying entire chain
..Improper hash on node 2 Does not begin with 000
Chain verification: false
Total execution time required to verify the chain was 1 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
5
Repairing the entire chain
Total execution time required to repair the chain was 51033 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-10-08 18:15:10.722","Tx ": "Carol pays Alice 1000 dscoin","PrevHash" : "","nonce" : 43,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-10-08 18:23:17.467","Tx ": "Alice pays Bob 100 dscoin","PrevHash" : "00324633B5875FF14A67B3C933E13F9C86FBCB02C85A87C64A8415BD88A35DDF","nonce" : 1188,"difficulty": 3},
{"index" : 2,"time stamp " : "2021-10-08 18:23:44.451","Tx ": "Frank pays Alice 3 dscoin","PrevHash" : "0001FCEAFB46C7D82E081F3B0E35C78143227A2F76FC06F6400A9F1BBD514C65","nonce" : 5946,"difficulty": 3},
{"index" : 3,"time stamp " : "2021-10-08 18:24:12.823","Tx ": "Alice pays Carol 23 dscoin","PrevHash" : "000D754052A3A957DE25A800E9F84980D95C2D7B70835B8A793D9DFFF836A61C","nonce" : 182685,"difficulty": 4},
{"index" : 4,"time stamp " : "2021-10-08 18:24:38.258","Tx ": "Donna pays Alice 34 dscoin","PrevHash" : "000013AD25EA66B6FC97128C251F31E5AE5F5B58317A9C092A2E744475A5E1DA","nonce" : 2039299,"difficulty": 5},
{"index" : 5,"time stamp " : "2021-10-08 18:26:27.032","Tx ": "Carol pays Donna 1 dscoin","PrevHash" : "00000A9DB3D01306AA378BABF91FD8CA7758D65E5C67A1E3ED605AFDEC818F7D","nonce" : 1013,"difficulty": 2},
{"index" : 6,"time stamp " : "2021-10-08 18:28:48.472","Tx ": "Edward pays Alice 34 dscoin","PrevHash" : "00DCE9D5166B60A32CDABB4D5BBED5CB3E65B6A1B15EE4D47003048FB7CDFC5F","nonce" : 106486,"difficulty": 4}
 ], "chainHash":"0000586C4EDC348F79E75815304F90D5535B2ACB3E624B50C30FD15904C55490"}

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
2
Verifying entire chain
Chain verification: true
Total execution time required to verify the chain was 0 milliseconds

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
0
Current size of chain: 7
Difficulty of most recent block: 4
Total difficulty for all blocks: 23
Approximate hashes per second on this machine: 1233045
Expected total hashes required for the whole chain: 1188352.000000
Nonce for most recent block: 106486
Chain hash: 0000586C4EDC348F79E75815304F90D5535B2ACB3E624B50C30FD15904C55490

0. View basic blockchain status.
1. Add a transaction to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the corruption by recomputing hashes.
6. Exit
6

Process finished with exit code 0


```
Label this second section **Task 0 Block.java** and include a complete listing of Block.java


Label this third section **Task 0 BlockChain.java** and include a complete listing of BlockChain.java

See the Javadoc's main routine. You are asked to experiment and provide some timing data and analysis. That commentary should be present in the comments of your main routine.

----

### Task 0 Grading Rubric 50 Points

Rubric:
1. The execution is correct and includes the same tests as above - in the same order (the name Alice has been replaced): 30 points.
2. The code is well documented: 5 points.
3. The analysis in the main routine is detailed and clear: 5 Points.
4. The code illustrates separation of concerns and good style: 5 points.
5. The single PDF file includes sections correctly labelled: 5 Points.  

## Task 1

The execution of Task 1 will appear exactly the same as in Task 0. The primary difference will be that, behind the scenes, there will be a client server interaction using JSON over TCP sockets. The blockchain will exist on the server. It will be constructed there and the client will make requests for operations over a TCP socket. The client will be focused on driving the menu driven interaction and communicating with the server on the backend.

You are required to design and use two JSON messages types - a message to encapsulate
requests from the client and a message to encapsulate responses from the server.

Use the following three labels in your single PDF:

**Task 1 Execution**

**Task 1 Client Source Code***

**Task 1 Server Source Code**

 -------


**Task 1 Grading Rubric 50 Points**

Rubric:
1. The execution is correct and includes the same tests as above - in the same order (the name Alice has been replaced) and a client server architecture based on TCP sockets is used. 30 points.
2. The JSON message being sent to the server is well designed: 5 Points
3. The JSON message being sent from the server to the client is well designed: 5 Points.
4. Separation of concerns is well done: 5 points.
5. The single PDF file includes sections correctly labelled: 5 Points.



**Project 3 Submission Requirements**

Name your IntelliJ project folders Project3Task0 and Project3Task1.

For each IntelliJ project, File->Export Project->To Zip... each. You must export in this way and NOT just zip the IntelliJ project folders.

You should now have two zip files:
* Project3Task0.zip
* Project3Task1.zip

And a single pdf named Project3.pdf.

Create a new empty folder named with your Andrew id (very important). Put the three files above into this new folder. Zip that folder, and submit it to Canvas.

**The file named YourAndrewID.zip contains two zips and a pdf:**
* Project3Task0.zip
* Project3Task1.zip
* Project3.pdf
