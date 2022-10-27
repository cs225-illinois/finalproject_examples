# Warning

This is a satirical proposal. You should only use it as an example of how to structure your own proposal. Do not copy this proposal.

## Leading Question 

Entropy is a measurable property associated with all objects and yet due to conservation of energy there is no existing solution to reversing entropy – progress towards disorder can never be reversed. Here we plan to use the totally-not-fake entropy database of all real-world objects (www.totallyrealwebsite.gov) to measure the average entropy of all objects and create a function capable of reversing entropy when given the entropy value of an object.

To visualize the average entropy of all objects, we will convert all objects into two-dimensional points (x,y) where x is a numeric representation of the object’s unique shape and location and y is a measure of its entropy. To reverse entropy, we will use a modified implementation of ActualScientist Shia Labeouf’s ’ShiaTransform’. If successful, we will be able to not only reverse entropy but also visualize this reversal through a dot-plot of all original entropies and all reversed entropies.

## Dataset Acquisition

The dataset we are using is the National Science Foundations (NSF) database of every object in the world (www.totallyrealwebsite.gov). As this dataset is very large, we will use a subset of data consistent of all objects found in the state of Illinois, a greatly reduced but still significant dataset.

## Data format

The original dataset consists of 42^100 distinct objects stored as a CSV file with five columns (name, x-position, y-position, z-position, and entropy). By using the x,y and z positions, we plan to filter the input database to only objects located in the state of Illinois. If this subset is still too large, we will define a smaller region as either a radius around Chicago or include individual cities and ignore rural regions of the state until we have a dataset of no more than 10 million objects.

We will then convert the x,y and z position into a single numerical value (distance from the center of Illinois) and throw out the ‘name’ column so that my dataset will be two-dimensional and much easier to process. This transformation does result in a loss of information – there is a sphere of points which are a fixed distance away from the center in 3D space – but is the only way to visualize entropy. Additionally, as the goal of the proposal is to reverse entropy, the fixed distance model will only affect visualization (as all entropies are left untouched).

## Data correction

Any object which is missing an x, y, or z value cannot be processed appropriately and will be thrown out. As ‘names’ are not relevant to our implementation, missing values for names can be ignored. If an object is missing an entropy value, we will take the average of the five closest objects by position as an approximation of that object’s entropy.

As an additional corrective measure, if the z-coordinate of an object is above 10,000 feet, we will ignore it as such objects are likely located on airplanes and do not technically constitute an object located in Illinois.

## Data storage

As my dataset is very large, it is important to store each object in as small of a space as possible. Under the assumption that many objects will have the same entropy value, we will use a Huffman encoding scheme on the entropies so that the most common entropies use the least amount of space. Each object can then be represented by two values – the float value defining the distance from the center of Illinois and a bitstring defining it’s entropy. The set of all such values will be stored in a two-dimensional list, where each row is a unique object and there is a column for distance and a column for the entropy code respectively. This will result in an O(n) storage cost for n objects.

As the entropies are encoded, there is an additional storage cost overhead in the form of a Huffman Tree defining the code. Assuming there are m unique entropies, this tree can be stored in O(m). As m ≤ n, the total storage cost for this project is still O(n), which allows us to store a significantly sized dataset.

## Algorithm 

To successfully implement this project we will need to code a Huffman Tree encoding, a data visualization step, and write ‘ShiaTransform‘ (Shia et al 2021).

### Huffman Tree 

The Huffman Tree implementation used is the class implementation from lab huffman but modified to use entropies as an input instead of strings. As the entropies are not sorted, this algorithm will take `O([REDACTED])` time but will still be O(m) in space for m unique entropy values. The output of the Huffman Tree algorithm is a paired encoding/decoding function that, given any entropy value will return the bitstring encoding of that entropy value (or vice-versa).

### Data Visualization

We do not know how we will visualize the data as there is not a clear algorithm or implementation based on our current knowledge. However, we will look into existing tools such as graphViz or write our own using some of the image handling code from mp_stickers and mp_mosaics.

Whatever the tool, our visualization function will take in a 2D list of positions and entropies (all objects in the dataset) and return a PDF graph. We expect our visualization function will take at most O(n) time to loop through (and plot) `n` distinct objects.

### ShiaTransform 

The ShiaTransform algorithm takes in a single entropy value and returns a modified entropy value as output. Conventionally, this takes O(1) time for a single object, so O(n) time in total. However in order to modify the ShiaTransform to reverse entropy, each object will need access to all nearby objects for a worst case run-time of O(n^2). Ideally, we will be able to do this without duplicating the dataset for a space complexity of O(1), but if necessary an additional factor of O(n) in space will be used as a lookup table.

## Timeline

We have already downloaded the target dataset, so the first step of the project will be performing the data correction and data storage steps. Together, these will take about a week so we plan to complete them by 13/48/77. The Huffman Tree will be coded up first and be complete by 13/55/77, followed by the data visualization of the original entropy values on 14/4/77. The Shia Transform may take a few weeks to complete and test but we hope to have it implemented by 14/18/77, alongside the data visualization of the reversed entropies. This gives us a week to write the final report and make my presentation before the final deadline of 14/32/77.
