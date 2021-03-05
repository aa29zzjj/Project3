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
running. These screenshots will aid the grader in evaluating your project. See below for a discussion of how to submit a video instead of a screen shot.


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
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Currupt the chain.
5. Hide the curruption by repairing the chain.
6. Exit

0
Blockchain status
Current size of chain: 1
Current hashes per second by this machine: 1293553
Difficulty of most recent block: 2
Nonce for most recent block: 436
Chain hash: 0008ABB5C043AF33AF40C857DBF7C5F89FED3A11DD91098C18766402E2E92339

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
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
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 12:09:03.33","Tx ": "Genesis","PrevHash" : "","nonce" : 436,"difficulty": 2}
 ], "chainHash":"0008ABB5C043AF33AF40C857DBF7C5F89FED3A11DD91098C18766402E2E92339"}

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

1
Add public key and decentralized identifier to the chain
Enter difficulty > 0 of this block
4
Enter RSA modulus (public key) in base 10.
977956222077584463804707148622512536126402477068218093398419
Public key: 977956222077584463804707148622512536126402477068218093398419
This is the computed decentralized identifier(DID): 1e1e86a6a568e9ae9a9f88826add7fed9be2a94e
Addding 977956222077584463804707148622512536126402477068218093398419,1e1e86a6a568e9ae9a9f88826add7fed9be2a94e to blockchain
Total execution time to add this block was 2129 milliseconds

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

1
Add public key and decentralized identifier to the chain
Enter difficulty > 0 of this block
5
Enter RSA modulus (public key) in base 10.
899971062532794907400701863056137027042839592731743635662461
Public key: 899971062532794907400701863056137027042839592731743635662461
This is the computed decentralized identifier(DID): 252b50d942c505365aca474a9078e63a25b87c27
Addding 899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27 to blockchain
Total execution time to add this block was 26846 milliseconds

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
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
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 12:09:03.33","Tx ": "Genesis","PrevHash" : "","nonce" : 436,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-03-05 12:11:24.823","Tx ": "977956222077584463804707148622512536126402477068218093398419,1e1e86a6a568e9ae9a9f88826add7fed9be2a94e","PrevHash" : "0008ABB5C043AF33AF40C857DBF7C5F89FED3A11DD91098C18766402E2E92339","nonce" : 83931,"difficulty": 4},
{"index" : 2,"time stamp " : "2021-03-05 12:12:27.17","Tx ": "899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "0000E6A879759886F39E8BEB6418EED2E925234F9B77F4A9CC38E1BA27119DEC","nonce" : 1074318,"difficulty": 5}
 ], "chainHash":"00000215B4FC2171AC849CFCE00C178C42533E02A3D6DA5402EF763B0E08D4CB"}

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

0
Blockchain status
Current size of chain: 3
Current hashes per second by this machine: 1982551
Difficulty of most recent block: 5
Nonce for most recent block: 1074318
Chain hash: 00000215B4FC2171AC849CFCE00C178C42533E02A3D6DA5402EF763B0E08D4CB

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
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
Enter new public key followed by a comma followed by a new DID
879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27
Block 1 now holds 879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 12:09:03.33","Tx ": "Genesis","PrevHash" : "","nonce" : 436,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-03-05 12:11:24.823","Tx ": "879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "0008ABB5C043AF33AF40C857DBF7C5F89FED3A11DD91098C18766402E2E92339","nonce" : 83931,"difficulty": 4},
{"index" : 2,"time stamp " : "2021-03-05 12:12:27.17","Tx ": "899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "0000E6A879759886F39E8BEB6418EED2E925234F9B77F4A9CC38E1BA27119DEC","nonce" : 1074318,"difficulty": 5}
 ], "chainHash":"00000215B4FC2171AC849CFCE00C178C42533E02A3D6DA5402EF763B0E08D4CB"}

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
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
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

5
Repairing the entire chain
Total execution time required to repair the chain was 4980 milliseconds

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

3
View the Blockchain
{"ds_chain" : [ {"index" : 0,"time stamp " : "2021-03-05 12:09:03.33","Tx ": "Genesis","PrevHash" : "","nonce" : 436,"difficulty": 2},
{"index" : 1,"time stamp " : "2021-03-05 12:11:24.823","Tx ": "879971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "0008ABB5C043AF33AF40C857DBF7C5F89FED3A11DD91098C18766402E2E92339","nonce" : 33552,"difficulty": 4},
{"index" : 2,"time stamp " : "2021-03-05 12:12:27.17","Tx ": "899971062532794907400701863056137027042839592731743635662461,252b50d942c505365aca474a9078e63a25b87c27","PrevHash" : "000027659C23D3D7EE662052C523984B43B2CC582DE066D8C6A63FA8C6CBE724","nonce" : 164510,"difficulty": 5}
 ], "chainHash":"000001A46DBA5F946C80B777AF41C74F1E8DF0F519B42D4F3AB406E761CC885F"}

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
2. Verify the blockchain.
3. View the blockchain.
4. Corrupt the chain.
5. Hide the curruption by recomputing hashes.
6. Exit

2
Verifying entire chain
Chain verification: true
Total execution time required to verify the chain was 0 milliseconds

0. View basic blockchain status.
1. Add a public key (RSA modulus) and DID to the blockchain. The DID is not entered but will be computed.
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

In a real blockchain implementation, the client would need to sign requests so that its account could be charged. In our example, the requests are requests to register public key and decentralized identifier pairs.

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

As an alternative to screenshots, you can create a screencast video of your working client and server. The video cannot be more than 3 minutes long. You may use an audio voiceover, but
you do not need to. You should publish the video as 'Unlisted' to YouTube.
(See more discussion on this in the Submission section below.) Include the URL
of the YouTube video in a document in the Project3Task0 Description folder
that you submit.

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
