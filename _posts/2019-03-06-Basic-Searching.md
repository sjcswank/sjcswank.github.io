---
published: false
---
## Searching For a Magic Door

I'm taking a break from string functions to start a series about search algorythms. Search algorithms are essential to most apps, weather mobile, web or desktop. Searching problems are also often used in the interview process. There are several different well established search algorythms ranging from the simple Linear Search to more complex Exponential Search, but there is always room for imporvement. Perhaps, at the end of this series, you'll be able to build a better mouse trap yourself.

### Linear Searching

The Linear Search Algorithm is one of, if not the simplest way to search. This algorithm starts at the left-most element of an array and compares the target value to to each element moving to the right until the target value is found. The benefits of a linear search include its simplicity and that it can be used on sorted, pivoted, and unsorted arrays. However, linear search is exceptionally slow and will often time-out when used on medium sized or large arrays and is therefore not often used in production.

You can easily look up a snippet of code for the linear search, but with the knowledge of how the search works, we can recreate the code for it on our own. As I always like to do with completely new bits of code, let's start with some pseudo code.

- Create a function that takes in an array arr[] and a target value x
- Start from the leftmost element of arr[] and 
- One by one compare x with each element of arr[]
	- If x matches with an element, return the index of that element.
- If x doesn’t match with any element, return -1.


We can take this pseudo code step by step and write out the actual code for the function. We start with defining the function. 

    public static int linearSearch(int arr[], int x){
    
    }


To run through the entire array from left to right we can use a for loop. Starting at the left-most index, index 0, we will continue looping through the array until we reach the end.

    public static int linearSearch(int arr[], int x){
    	for(int i = 0; i < arr.length; i++){
        
        }
    }


For each index we need to compare the value of x to the value at that index. If the values match, we need to stop the loop and return the number of the index.
	
    public static int linearSearch(int arr[], int x){
    	for(int i = 0; i < arr.length; i++){
        	if (x == arr[i])
            	return i;
        }
    }

Lastly, if we reach the end of the array and exit the for loop without returning anything, we know that the target element is not in the array and we should return -1. We use -1 because it is an integer that will never be an index of the array.
	
    public static int linearSearch(int arr[], int x){
    	for(int i = 0; i < arr.length; i++){
        	if (x == arr[i])
            	return i;
        }
        return -1;
    }

### Testing Our Function

Testing a peice of code if imperative. We'll run the function a few times with different values and arrays and make sure we get the right returns. 
	
    public static int linearSearch(int arr[], int x){
    	for(int i = 0; i < arr.length; i++){
        	if (x == arr[i])
            	return i;
        }
        return -1;
    }
    
    public static void main(String args[]){
    
    int x = 5;
    int arrX[] = {1, 3, 5, 7, 9, 11};
    
    System.out.println(linearSearch(arrX, x));
    
    int y = 3;
    int arrY[] = {5, 3, 7, 9, 30};
    
    System.out.println(linearSearch(arrY, y));
    
    int z = 4;
    int arrZ[] = {6, 12, 9, 16, 20};
    
    System.out.println(linearSearch(arrZ, z));
    
    }

We should see the following printed to the console:
	
    3
    1
    -1
    
As we saw, linear search is effective on both sorted and unsorted arrays. We kept our arrays short for ease of testing and so that we wouldn't run into an issues with processing time if we loop through the whole array. Let's try one more time with an array that has more than one instance of the target variable:

	int x = 5;
    int arr[] = {1, 3, 5, 5, 3, 1};
    
    System.out.println(linearSearch(arr, x));
	

This should return 2, and only 2. Linear search returns once it finds a match, so the remaining elements in the array aren't tested and only the index of the first instance of the array is returned.

Linear search is simple and limited, but a great starting point for the next search I'll be covering, Binary Search. For now, see if you can figure out a way to improve on the linear search on your own. And be sure to swing back around next week for more coding fun.

Thanks for reading and happy coding!