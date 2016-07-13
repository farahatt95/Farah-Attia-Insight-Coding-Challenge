#Farah Attia Insight Coding Challenge

I realized too late that another solution to the problem would be to build a balanced max heap from the incoming data payments, with the degree of the node attached to the nodes, and then use extract_max in order to find the median each time, as each JSON is processed.

**The files are in the folder coding-challenge-master.** My functions and classes are in the Extract_Info file under src. **In this file, I imported ast, datetime, and json.** In src, I also have a tests file for testing purposes.

I had to use the relative path '..\\insight_testsuite\\tests\\test-1-venmo-trans\\venmo_output' for output.txt and the same but with 'venmo_input' substituted in in order to pass the tests provided in the test suite (see lines 116 and 176 in Extract-Info.py). I am not sure if that will work for other tests that you will be testing us with or if the location is still too specific, but I didn't reference specific paths in my system, only folders that I uploaded here.

I have two classes, Node and Graph. My nodes are represented by the actor. My graph is represented as a dictionary where nodes are keys and values are lists of nodes that they are connected to.

I have several functions which assist the "main" function. These include get_information, which changes the textfile of JSON messages into a list of lists returned by get_information. Each of the lists in the master list, like the JSON messages contains an actor, target, and created time. 

There is also find_max_time, to find the larger of two times, and within_sixty, which determines if two times are within 60 seconds of each other. Find_median finds the median in a list.

Main is the main function, which takes in a text file and goes through the master list returned by get_information, which also takes in a textfile, and finds the median at each point in the list (after each payment is processed). The process of the function is to find the median of the list is that it goes through each of the lists in the master list, where each list is a payment containing actor, target, and created time. In the list, the index for actor was always 0, for target, 1, and for time, 2, so that I could easily access them. From there, I check if the time of the payment is greater than the current maximum time, which I initialize to be “mindate” which occurs in MINYEAR of January 1st, where the hour, minute, and second fields are equal to zero. If the time of the payment is within 60 seconds of the maximum, then I create two nodes, of the actor and the target, add them to the graph if they are not already there, and connect them. Then I go through the list of nodes in the graph and remove all instances of any node that is no longer in the 60 second time window. I then go through the nodes again, getting the degrees of them and adding them to the list. In the end, I find the median of the list of degrees, add that to a master list and then write those medians to the output.txt file.
