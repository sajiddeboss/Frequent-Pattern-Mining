About Pattern Mining Algorithms
Apriori algorithm: 
- This approach is used to find the dataset's most frequent item sets and allows us to derive 
association rules from them. It employs prior knowledge of frequent items and utilizes an 
iterative strategy to find K+1 item sets from a set of K frequent things. The Apriori 
algorithm's main idea is that all subsets of a frequent itemset must also be frequent. 
FP growth algorithm: 
- To solve the shortcoming of the Apriori method, the Frequent pattern algorithm uses a 
divide-and-conquer strategy to locate the most frequent pattern in the dataset by creating 
frequent item sets with the minimum support. It generates an FP-tree that preserves the 
item's relationship and separates the dataset into a series of conditional pattern bases, each 
connected with one frequent item, for which only the related datasets must be scanned for 
patterns.

Implementation of Apriori algorithm:
1. Initialize a dictionary, which stores our frequent pattern item sets.
2. Fetch the transactions from each rows of the dataset provided, remove duplicate items 
within the transaction and also count the total number of transaction, and store in the 
transaction and transaction_counter variables respectively.
3. Create a dictionary that stores all the individuals item sets, and its number of occurrence in 
the dataset.
4. From the dictionary, created above we keep only the items that obliges the minimum 
support threshold and these items are updated into the frequent dictionary initialized in the 
step 1.
5. Generate the candidate keys with k values of items in a itemset , from items generated in 
the previous step and repeated the steps 3 and 4 to generate the frequent pattern in the 
dataset and update the dictionary.
6. Within a while loop, increment the k and repeat the step 5, until no frequent pattern is 
generated
7. Print the frequent generated.

Implementation of Improved Apriori algorithm:
To overcome the longer runtime and multiple scans of the databases, instead of running the 
algorithm over whole dataset, we took a sample of the dataset and run the algorithm in this sample 
data and generate the frequent pattern. Though the accuracy might reduce, but the runtime of the 
algorithm is reduced drastically. A sample of 500 data entries is given the apriori algorithm 
implemented in the previous section. We may also perform other improvements like partitioning 
the database into n parts and generating the frequent patterns of all n parts.

Implementation of FP Growth algorithm:
1. The first step is similar to the apriori algorithm, where the whole dataset is scanned and the 
item with minimum support count is taken, Create a dictionary that stores all the individuals 
item sets, and its number of occurrence in the dataset and this is stored in the header table 
in the descending order of the count.
2. Create the FP-tree, by initializing a node with null datapoint. For each item in the header 
table update the fptree by creating new node and adding it to the proper prefix path and 
also increment the count if the item already exists in the tree, further also store the child of 
the each node if it exists.
3. After completing the construction of the FP-tree, mine the tree for conditional pattern bases 
by starting with the items that has lowest count and then finding all of its prefix path. Then 
this is repeated for all the items in the header table.
4. Return the frequent pattern which has higher support than the user defined minimum 
support.

Dataset used to test the algorithms: 
To perform the frequent Itemset mining, we use UCI adult dataset. It consists of 32562 entries 
and 15 columns. Since we are interested in find the frequent pattern, in the data preprocessing step 
we remove all the rows with null values and also drop the columns with numerical values. Hence 
after the data cleaning step, we get a dataset of size 32561*9 which is fed into the pattern mining 
algorithm. Ronny Kohavi and Barry Becker collected this information from the 1994 Census 
Bureau database (Data Mining and Visualization, Silicon Graphics). The aim is to forecast whether 
a person earns more than $50,000 per year.(http://archive.ics.uci.edu/ml/datasets/Adult)

