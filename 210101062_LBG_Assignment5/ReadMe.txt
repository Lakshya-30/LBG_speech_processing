-------------------------------------- CS566 ASSIGNMENT 5------------------------------------------------
NAME: Lakshya Onkara
ROLL NO.: 210101062

AIM: Vector quantization using LBG algorithm
EXECUTION: Build and run the code on Visual Studio 2010. Use F5 key to run the code.

INPUT: Universe.csv
OUTPUT: A codebook of distinct analysis vectors.

CONSTANTS:
1. DELTA: Used to terminate the K-means algorithm (0.0001)
2. P: The number of past samples to consider (12)
3. k: Size of the codebook (8)
4. tokhuraWeights: Array to store the 12 Tokhura weight values.
5. M: Size of the universe.
6. EPSILON: The splitting parameter (0.03)

VARIABLES:
1. universe: Vector of vectors to store input values.
2. codebook: Vector of vectors to store the code vectors.
3. clusters: Vector of vectors to store the assignment of vectors to regions.
4. prevCodebook: Vector of vectors to store the previous codebook.

FUNCTIONS:
1. printCodebook():
	Function to print the code vectors.

2. readUniverse():
	Function to read the input .csv file and store the input in universe vector.

3. tokhuraDistance():
	Function to calculate the Tokhura distance between the current centroid and current row of universe.

4. nearestNeighbors(): 
	Function to assign vectors of the universe to a cluster on the basis of minimum tokhura distance.

5. totalDistortion():
	Function to calculate the average total distortion.

6. updateCodeVector():
	Function to update the code vectors to minimise distortion.

7. kMeans():
	Function to implement Lloyd's algorithm for vector quantization.

8. splitCentroid():
	Function to double the size of the codebook by splitting each current code vector.

9. LBGAlgo():
	Function to implement the LBG algorithm.


PROCEDURE:
1. Start with a single vector representing the centroid of the universe. At this point, the codebook will contain one vector of 12 values.
2. Double the codebook size by following the steps below for each entry in the current codebook:
a) One vector will be obtained by Yi = Yi(1 + epsilon)
b) Another vector will be obtained by Yi = Yi(1 - epsilon)
(Here, i ranges from 1 to p = 12, epsilon = 0.03.)
3. Apply the K-means algorithm to refine the centroids for the newly split codebook (which will be double the size of the previous step's codebook).
Repeat this process until the codebook size reaches k.