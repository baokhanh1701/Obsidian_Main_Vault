## Double iteration
Iterate i from 0 -> end
	iterate j from i -> end
		find duplicate

## Sort
Sort first --> then iterate to find duplicate value arr[i] == arr[i+1]

## Set
Set cannot contains duplicate elements.
Make a set and compare the vector size with the set size to determine:
	if the set size is smaller than the original size => contain duplicate

## Hash
Create a key - value map, with:
key: number in vector
value: number of occurences of the key
	if value of a key > 2 => contains duplicates