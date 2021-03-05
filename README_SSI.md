# 95-702 Distributed Systems For Information Systems Management
# Project 3 Spring 2021


Assigned: Friday, March 5, 2021
Due Friday, March 19, 11:59pm


**Principles**
One of our primary objectives in this course is to make clear the fundamental
distinction between functional and nonfunctional characteristics of distributed
systems. The functional characteristics describe the business or organizational
purpose of the system. The non-functional characteristics affect the quality of
the system. Is it fast? Does it easily interoperate with others? Is it fault
tolerant? Is it reliable and secure?

In this project, we will illustrate an important nonfunctional characteristic
of blockchain technology - its tamper evident design. We will build a stand-alone
blockchain (Task 0) and a distributed system where a remote client interacts
with a blockchain API (Task 1).
The student should note that this is not all of blockchain. There is more to
learn. Real blockchains are decentralized and include peer to peer communication and many replicas of
the blockchain. The blocks themselves typically include Merkle Trees. This
assignment does not do all of that but it does provide a solid foundation to build on.

**Overview**
In Task 0, you will write a blockchain by carefully following the directions in
Javadoc format found here:
http://www.andrew.cmu.edu/course/95-702/examples/javadoc/index.html

The Javadoc describes two classes that you need to write - Block.java and BlockChain.java.
In Task 1, you will distribute the application that you created in Task 0. You
will write a client server application. The interaction between the client and
the server will be  with JSON messages over TCP sockets. Thus, your work from
Project2, Task 5 will be very useful and may be reused here.
For each task below, you must submit screenshots that demonstrate your programs
running. These screenshots will aid the grader in evaluating your project.

Alternatively, you can create a screencast video of your working client and server.
The video cannot be more than 3 minutes long. You may use an audio voiceover, but
you do not need to. You should publish the video as 'Unlisted' to YouTube.
(See more discussion on this in the Submission section below.) Include the URL
of the YouTube video in a document in the Project3Task0 Description folder
that you submit.

Documenting code is also important. Be sure to provide comments in your code
explaining what the code is doing and why. Be sure to separate concerns when
appropriate. You may include the Javadoc comments (provided) in your own code.
But you are required to comment on any additions or modifications that you make.

Any code from external sources, e.g., stack overflow, must be cited with a URL.

**Task 0 Execution**
Write a solution to Task 0 by studying the Javadoc provided on the course
schedule. The logic found in Task 0 will be reused in Task 1.
The execution of Task 0, a non-distributed stand-alone program, will look
almost exactly like the following interaction. You will select the exact
same options and enter the exact same transactions. The only differences,
of course, will be those due to the dynamic computations associated with
the blockchain. As part of the submission of Task 0, you must turn in a
screenshot (or screencast) such as the following:

```
run:

0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Currupt the chain.
5. Hide the curruption by repairing the chain.
6. Exit  

0

Current size of chain: 1  
Current hashes per second by this machine: 885873  
Difficulty of most recent block: 2  
Nonce for most recent block: 326  
Chain hash: 003A1CDB1FED878153583435C6E74CB4C9884E61F872F49A5FBB1BD9382BF910  

0. View basic blockchain status.  
1. Add a public key to the blockchain.  
2. Verify the blockchain.  
3. View the blockchain.  
4. Corrupt the chain.  
5. Hide the curruption by recomputing hashes.  
6. Exit  
2
Verifying entire chain
Chain verification: true
Total execution time required to verify the chain was 2 milliseconds
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 11:22:42.437","Tx ": "Genesis","PrevHash" : "","nonce" : 326,"difficulty": 2}
 ], "chainHash":"003A1CDB1FED878153583435C6E74CB4C9884E61F872F49A5FBB1BD9382BF910"}
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
4
Enter RSA modulus (public key)
977956222077584463804707148622512536126402477068218093398419
Public key: 977956222077584463804707148622512536126402477068218093398419
Decentralized Identifier(DID): 1e1e86a6a568e9ae9a9f88826add7fed9be2a94e
Addding 977956222077584463804707148622512536126402477068218093398419,1e1e86a6a568e9ae9a9f88826add7fed9be2a94e to blockchain
Total execution time to add this block was 1477 milliseconds
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
1
Enter difficulty > 0
4
Enter RSA modulus (public key)
899971062532794907400701863056137027042839592731743635662461
Public key: 899971062532794907400701863056137027042839592731743635662461
Decentralized Identifier(DID): 252b50d942c505365aca474a9078e63a25b87c27
Addding 899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27 to blockchain
Total execution time to add this block was 1164 milliseconds
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
2
Verifying entire chain
Chain verification: true
Total execution time required to verify the chain was 1 milliseconds
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 11:22:42.437","Tx ": "Genesis","PrevHash" : "","nonce" : 326,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-03-05 11:23:43.349","Tx ": "977956222077584463804707148622512536126402477068218093398419,1e1e86a6a568e9ae9a9f88826add7fed9be2a94e","PrevHash" : "003A1CDB1FED878153583435C6E74CB4C9884E61F872F49A5FBB1BD9382BF910","nonce" : 52979,"difficulty": 4},
{"index" : 2,"time stamp " : "2021-03-05 11:25:27.613","Tx ": "899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "000061D2E1816162060C71390A96C6AE41D6AED5E336547B8C614AE9F2931EA4","nonce" : 48646,"difficulty": 4}
 ], "chainHash":"000039DE6998EF238B22B74BAC37CC4E0D41B7D398976358B5DAAB28C4C64EA2"}
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
0
Current size of chain: 3
Current hashes per second by this machine: 920262
Difficulty of most recent block: 4
Nonce for most recent block: 48646
Chain hash: 000039DE6998EF238B22B74BAC37CC4E0D41B7D398976358B5DAAB28C4C64EA2
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
4
Currupt the Blockchain
Enter block ID of block to currupt
1
Enter new data for block 1
879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27
Block 1 now holds 879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 11:22:42.437","Tx ": "Genesis","PrevHash" : "","nonce" : 326,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-03-05 11:23:43.349","Tx ": "879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "003A1CDB1FED878153583435C6E74CB4C9884E61F872F49A5FBB1BD9382BF910","nonce" : 52979,"difficulty": 4},
{"index" : 2,"time stamp " : "2021-03-05 11:25:27.613","Tx ": "899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "000061D2E1816162060C71390A96C6AE41D6AED5E336547B8C614AE9F2931EA4","nonce" : 48646,"difficulty": 4}
 ], "chainHash":"000039DE6998EF238B22B74BAC37CC4E0D41B7D398976358B5DAAB28C4C64EA2"}
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
2
Verifying entire chain
..Improper hash on node 1 Does not begin with 0000
Chain verification: false
Total execution time required to verify the chain was 1 milliseconds
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
5
Repairing the entire chain
Total execution time required to repair the chain was 8397 milliseconds
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 11:22:42.437","Tx ": "Genesis","PrevHash" : "","nonce" : 326,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-03-05 11:23:43.349","Tx ": "879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "003A1CDB1FED878153583435C6E74CB4C9884E61F872F49A5FBB1BD9382BF910","nonce" : 170023,"difficulty": 4},
{"index" : 2,"time stamp " : "2021-03-05 11:25:27.613","Tx ": "899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "0000F4E30641FDF58E3E3273FB2164A91CABDAA05B2342230436C2CC2DFEB5F1","nonce" : 179755,"difficulty": 4}
 ], "chainHash":"0000ED7D5270EDFA9EC76DBB3AF3E52D618D50B399CFBC5B5700416AEE896461"}
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
2
Verifying entire chain
Chain verification: true
Total execution time required to verify the chain was 1 milliseconds
0. View basic blockchain status.
1. Add a public key to the blockchain.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit
6

Process finished with exit code 0
```

**Task 0 Grading Rubric 50 Points**

See the Javadoc for a description of the main routine and the difficulty levels.


|                   |Excellent|Good|Poor|No submission|
|-------------------|---------|----|----|-------------|
|Screenscrape shows exact|44       | 40 | 30 | 0           |
|same execution|||||
||||||
|Blockchain main method well documented and|4|3|2|0|
|describes behavior with difficulty levels of 4 and 5|||||
||||||
|Separation of concerns and good style|1|0|0|0|
||||||
|Submission requirements met|1|0|0|0|


**Task 1 Execution**

The execution of Task 1 will appear exactly the same as in Task 0. The primary
difference will be that, behind the scenes, there will be a client server interaction
using JSON over TCP sockets.

Use Project 2, Task 5 as a guide. Each request to the server must be signed using
the private key as was done in Project 2, Task 5. The signature must be checked
on the server. If the signature fails to verify, send an appropriate error message
back to the client.

You are required to design two JSON messages types - a message to encapsulate
requests from the client and a message to encapsulate responses from the server.
Each JSON request message will include a signature. You need not sign the response to the client.


**Task 1 Grading Rubric 50 Points**



|                   |Excellent|Good|Poor|No submission|
|-------------------|---------|----|----|-------------|
|Screenscrape shows client server and|40       | 36 | 30 | 0           |
|exact same execution as Task 0|||||
||||||
|Request response JSON message format designed well|4|3|2|0|
||||||
|Server verifies ID and signature on each request|4|3|2|1|
|Separation of concerns and good style|1|0|0|0|
||||||
|Submission requirements met|1|0|0|0|


**Project 3 Submission Requirements**

Documentation of code is always required.

Remember to separate concerns. Break your code up into chunks where each chunk does one thing well.


Video sharing rights: If you are creating screencast videos, then you should set the YouTube sharing rights 'Unlisted' when publishing to YouTube. There are three types of sharing rights on YouTube: Public, Private and Unlisted. You do not want other students to be able to see your video (that would be cheating), and ‘Unlisted’ restricts viewing to only those who have your URL.

Be sure you have named your IntelliJ project folders correctly.  
For each IntelliJ project, File->Export Project->To Zip... each. You must export in this way and NOT just zip the IntelliJ project folders.

**You should also have two description folders:**
* Project3Task0 Description
* Project3Task1 Description

Each description folder contains either a single document (you may choose an appropriate name) with screenshots showing the execution of Task 0 and Task 1 or a link to a video showing your work. (If you upload your video to YouTube, make sure your video is selected as ‘unlisted’.)

**You should also have two zip files:**
* Project3Task0.zip
* Project3Task1.zip

Create a new empty folder named with your Andrew id (very important). Put all files mentioned above into this new folder. Zip that folder, and submit it to Canvas. The submission should be a single zip file. Now you should have only one zip file named with your Andrew id.

**The file named YourAndrewID.zip contains:**
* Project3Task0.zip
* Project3Task1.zip
* Project3Task0 Description (Folder)
* Project3Task1 Description (Folder)
