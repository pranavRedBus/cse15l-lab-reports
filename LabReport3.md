# Part 1 (`reversed()` in `Array Examples`)


## - A Failure-Inducing Input
> 
> 
      @Test
      public void testReversed() {
     
        int[] input1 = {1,2,3,4,5};
     
        assertArrayEquals(new int[]{5,4,3,2,1}, ArrayExamples.reversed(input1));
     
      }


## - A Working Input
> 
> 
      @Test
      public void testReversed() {
     
        int[] input1 = { };
     
        assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
     
      }


## - Symptom
-   Working Output
![ReverseWorksTest](ReverseWorksTest.png)

-   Failure Output
![ReverseFailure](ReverseFailure.png)


## - Bug
-   Before
> 
>
    static int[] reversed(int[] arr) {

        int[] newArray = new int[arr.length];
    
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = newArray[arr.length - i - 1];
        }
        return arr;
    }

- After
>
>
    static int[] reversed(int[] arr) {
      
        int[] newArray = new int[arr.length];
    
        for(int i = 0; i < arr.length; i += 1) {
          newArray[arr.length - i - 1] = arr[i];
        }
      
        return newArray;
    }

- Explanation of Fix
  The fix above works as the original code's bug was that it didn't rigorously test the `reverse()` method at all, creating an empty array to feed into it but not a comprehensive, filled array. By making this switch, I ensure that when the code is passed in with a 5 element `int[]` array, it properly returns the reverse copy of that array, checking with the hand-checked reversed array in the test method. 

# Part 2 (Researching `less`)
