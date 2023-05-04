Download Link: https://assignmentchef.com/product/solved-cs69012-assignment6-map-reduce
<br>
This assignment is on map-reduce, which is a distributed and scalable way of extracting/mining required information from multiple datasets stored on multiple servers. Follow the tutorial to understand how you can design mapper and reducer for specific queries/operations.

Tutorial on map-reduce

You can start with a simple word count problem. Say, we have a text file and we want to count the frequency of occurrence of each word. The tutorial below explains how to solve this problem using a map-reduce algorithm. <strong><em>Tutorial References ​</em></strong>:

<a href="http://www.michael-noll.com/tutorials/writing-an-hadoop-mapreduce-program-in-python/">http://www.michael-noll.com/tutorials/writing-an-hadoop-mapreduce-program-in-python/</a> Next you can also look into the following tutorial for slightly harder query (tf-idf scores) <a href="https://www.tutorialspoint.com/map_reduce/map_reduce_tutorial.pdf">https://www.tutorialspoint.com/map_reduce/map_reduce_tutorial.pdf</a>

<h2>Tasks</h2>

<ol>

 <li>Study HDFS and MapReduce basics.</li>

 <li>Write the necessary mapper and reducer routines in python to implement the queries mentioned in later sections.</li>

 <li>Ensure that the reducer routine prints results of queries to a text file (as asked in the later sections).</li>

</ol>

<strong> </strong>Dataset

We will be using a dataset on a Facebook (FB) network with ​<strong>3,892</strong> users. Please download the​    data “network.txt”. You have to extract required information from this data. Below is a sample of data available in the file.

<h2>(​network.txt​)</h2>

0,1838

0,1744 0,14

0,2543

1,1009

1,1171

1,1465

where

<ul>

 <li>Each line represents an ​<strong>undirected edge​</strong> between two users indicated by two node-ids separated by a comma. So, no pair of nodes are repeated in the file.</li>

</ul>

<h2>Sample code to read the files</h2>

import gzip fp=open(“network.txt”) for line in fp:

l_arr=line.split(“,”)      node1=l_arr[0]      node2=l_arr[1]

<h2>Queries</h2>

The queries are to be implemented in the mapper and reducer phases. Some of them may give empty results. You need to implement the following queries in this assignment. The queries have an imaginary backstory to help you find a real world perspective in this assignment.

<ol>

 <li>You are the CEO of a car company. You want to run an advertisement campaign on FB for your newly launched car. An FB official tells you that if you choose to send the ads to all users each with at least 20 friends, then they will charge you INR 100 per user. You want to calculate how much you will have to spend for your ad campaign if you choose to float ads only for users with at least 20 friends. Write mapper and reducer routines for this. (Hint: Count all the users (node-ids) with at least 20 friends using mapper and reducer, and then multiply 100 with that before printing the output)</li>

</ol>




<ol start="2">

 <li>The FB official also gives you a free welcome offer valid only for once. This offer is for you to judge the impact of advertising on FB. They say they will send your ad to any 10 users as per your selection. You are a very intelligent business person. So, you think that if you send your ads to users who have a large number of friends, then your ad will easily spread through FB shares, and you won’t have to pay anything for the paid ad campaign. So, you want to find the top-10 users (node-ids) with the highest number of friends (order doesn’t matter). Write mapper and reducer routines for this.</li>

</ol>

3. After you exploit the free offer, immediately FB realizes the flaw in the offer, and discontinues it. However, your ad has already gone to the top-10 users. Now, FB being a very manipulative company, decides to hide your ad from the newsfeed of the users who are connected to the top-10 users, so that even if the top-10 users share your ad, it won’t be visible to others and it won’t spread. So, FB wants to find out the users who have friendship with at least one out of the top-10 users. Write mapper and reducer routines for this. (Hint: the mapper can use the list obtained in the last query).

4. Even though FB makes all the effort to stop your ad from spreading, by the time FB is able to change the newsfeeds of the users, your ad has already spread to a part of the FB network. As your trick has worked, you are now very happy, and you spend most of your advertising budget in organizing parties. However, you suddenly realize that, in the US, there is no demand for your car. You find out that even if your ad has spread to a part of the FB network, it has not gone to any user in the US which is the biggest market for your company. You, then, run back to the FB official. Looking at your situation and your previous endeavour, FB wants to teach you a lesson. The FB official tells you that they will now charge you ​<strong>INR ​</strong><strong>10*X</strong> to show your ad to ​​ <strong>a user with ​</strong><strong>X number of friends​</strong>​        . After spending most of the advertising budget, you decide to send your ad only to top-10 US users with the highest number of friends in the US. In this regard, your company’s board of directors want to know how much will be required for this task. You know that all the users with node-id between 0 and 999 are the only users from the US. Write mapper and reducer routines to find out how much you will have to spend to send your ad to the top-10 US users with the highest number of friends in the US.

<strong>How to run and test your code:  </strong>

Since we do not have access to a Hadoop cluster, we will be testing our codes on a Linux system as follows: cat network.txt | python mapper.py | sort | python reducer.py  &gt; result.txt  Or just ​python mapper.py | sort | python reducer.py &gt; result.txt

<u>Explanation on the above commands:</u>

<ol>

 <li>“cat” is a linux command to print the contents of a file on the console.</li>

 <li>The pipe operator (|) directs the output of the previous command to the next command.</li>

 <li>“sort” is a linux command to sort the input lexicographically. 4. “&gt;” can be used to save the standard output in a file.</li>

</ol>

<strong>Deliverables​</strong>: 4 sets of python codes (mapper and reducer), 4 Makefiles, 4 result.txt, 1 readme

<strong>Evaluation Scheme​</strong>: Results: 90 marks,​ ​Coding Style: 10 marks