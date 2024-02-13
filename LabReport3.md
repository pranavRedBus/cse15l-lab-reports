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

- **Explanation of Fix:** 
  The fix above works as the original code's bug was that it didn't rigorously test the `reverse()` method at all, creating an empty array to feed into it but not a comprehensive, filled array. By making this switch, I ensure that when the code is passed in with a 5 element `int[]` array, it properly returns the reverse copy of that array, checking with the hand-checked reversed array in the test method. 

# Part 2 (Researching `grep`)
1. ## Command 1: `grep -l` (Found using `man grep`)
- **Source Used**: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**: `grep -l` lists the names of the files, rather than the direct lines from the files, which contain the specified string. In this case, grep -r recursively searches the `technical` directory for matches to *''base pairs''*, and `-l` forces the output to list the names of the files, rather than each line in the file that contains the phrase. 
>
> 
      pranavrb@Pranavs-MacBook-Pro technical % grep -r -l  "base pair" .          
            ./plos/journal.pbio.0020223.txt
            ./plos/journal.pbio.0020190.txt
            ./biomed/1471-2156-2-3.txt
            ./biomed/1471-2121-3-10.txt
            ./biomed/gb-2001-2-4-research0010.txt
            ./biomed/gb-2003-4-4-r24.txt
            ./biomed/gb-2001-2-4-research0011.txt
            ./biomed/1471-2229-2-3.txt
            ./biomed/gb-2001-2-7-research0025.txt
            ./biomed/1471-2458-3-5.txt
            ./biomed/1471-2199-2-12.txt
            ./biomed/gb-2001-2-3-research0008.txt
            ./biomed/gb-2001-2-8-research0027.txt
            ./biomed/1471-2350-2-2.txt
            ./biomed/1472-6750-1-13.txt
            ./biomed/1471-2474-2-1.txt
            ./biomed/1471-2156-3-16.txt
            ./biomed/ar297.txt
            ./biomed/bcr631.txt
            ./biomed/gb-2001-2-4-research0014.txt
            ./biomed/1471-2156-2-7.txt
            ./biomed/1471-2105-4-27.txt
            ./biomed/ar409.txt
            ./biomed/1471-2164-4-21.txt
            ./biomed/1471-2180-3-15.txt
            ./biomed/1471-2202-2-12.txt
            ./biomed/1471-2180-1-12.txt
            ./biomed/1471-2105-2-9.txt
            ./biomed/1471-2105-2-8.txt
            ./biomed/gb-2002-3-12-research0079.txt
            ./biomed/1471-2164-3-13.txt
            ./biomed/gb-2001-2-6-research0021.txt
            ./biomed/gb-2002-3-12-research0083.txt
            ./biomed/1471-2180-3-13.txt
            ./biomed/1471-2377-3-4.txt
            ./biomed/1471-2164-4-25.txt
            ./biomed/1471-2156-3-4.txt
            ./biomed/1471-213X-1-4.txt
            ./biomed/1471-2210-2-14.txt
            ./biomed/1471-2180-1-31.txt
            ./biomed/1475-4924-1-5.txt
            ./biomed/1471-2164-4-14.txt
            ./biomed/1471-2164-3-35.txt
            ./biomed/1471-2164-4-16.txt
            ./biomed/ar774.txt
            ./biomed/gb-2000-1-1-research002.txt
            ./biomed/1471-2105-3-18.txt
            ./biomed/1471-2105-3-24.txt
            ./biomed/1471-2199-3-17.txt
            ./biomed/1471-2164-3-31.txt
            ./biomed/1471-2164-3-6.txt
            ./biomed/1471-2156-2-17.txt
            ./biomed/gb-2002-3-6-research0029.txt
            ./biomed/1471-2121-1-2.txt
            ./biomed/1471-2180-1-34.txt
            ./biomed/1471-2164-3-7.txt
            ./biomed/1471-2202-3-7.txt
            ./biomed/1471-2334-3-12.txt
            ./biomed/1471-2164-2-1.txt
            ./biomed/1477-7827-1-23.txt
            ./biomed/bcr602.txt
            ./biomed/1471-2091-3-4.txt
            ./biomed/gb-2001-2-12-research0054.txt
            ./biomed/1471-2105-3-2.txt
            ./biomed/gb-2002-3-10-research0053.txt
            ./biomed/rr196.txt
            ./biomed/bcr571.txt
            ./biomed/1471-2180-2-38.txt
            ./biomed/1471-2164-2-7.txt
            ./biomed/1471-2199-2-5.txt
            ./biomed/bcr570.txt
            ./biomed/1471-2202-3-16.txt
            ./biomed/1471-2180-2-13.txt
            ./biomed/1471-2350-2-8.txt
            ./biomed/1471-2164-2-4.txt
            ./biomed/1471-2164-4-2.txt

- **Example 2**: `grep -l` lists the names of the files, rather than the direct lines from the files, which contain the specified string. In this case, grep -r recursively searches the `plos` directory for matches to *''base pairs''*, and `-l` forces the output to list the names of the files, rather than each line in the file that contains the phrase. 
>
>
      pranavrb@Pranavs-MacBook-Pro technical % grep -r  -l "base pair" ./plos  
            ./plos/journal.pbio.0020223.txt
            ./plos/journal.pbio.0020190.txt

2. ## Command 2: `grep -c` (Found using `man grep`)
- **Source Used**: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**:
>
>
      pranavrb@Pranavs-MacBook-Pro technical % grep -c  "the" ./biomed/rr74.txt
            102

- **Example 2**:
>
>
      pranavrb@Pranavs-MacBook-Pro technical % grep -r -c "the" ./plos   
            ./plos/pmed.0020273.txt:25
            ./plos/journal.pbio.0030032.txt:74
            ./plos/pmed.0020065.txt:29
            ./plos/pmed.0020071.txt:57
            ./plos/pmed.0020059.txt:269
            ./plos/pmed.0010039.txt:93
            ./plos/journal.pbio.0020354.txt:77
            ./plos/pmed.0010010.txt:88
            ./plos/journal.pbio.0020156.txt:71
            ./plos/pmed.0020104.txt:43
            ./plos/pmed.0020272.txt:40
            ./plos/pmed.0020258.txt:22
            ./plos/pmed.0020099.txt:64
            ./plos/journal.pbio.0020140.txt:90
            ./plos/journal.pbio.0020183.txt:86
            ./plos/journal.pbio.0020430.txt:48
            ./plos/journal.pbio.0020394.txt:135
            ./plos/journal.pbio.0020431.txt:74
            ./plos/journal.pbio.0020419.txt:106
            ./plos/pmed.0010013.txt:73
            ./plos/pmed.0020113.txt:21
            ./plos/journal.pbio.0020169.txt:112
            ./plos/pmed.0020098.txt:61
            ./plos/journal.pbio.0020035.txt:116
            ./plos/pmed.0020067.txt:88
            ./plos/pmed.0020073.txt:232
            ./plos/journal.pbio.0030024.txt:92
            ./plos/journal.pbio.0020223.txt:72
            ./plos/pmed.0020249.txt:266
            ./plos/pmed.0020275.txt:29
            ./plos/journal.pbio.0020019.txt:85
            ./plos/pmed.0020088.txt:45
            ./plos/journal.pbio.0020145.txt:118
            ./plos/pmed.0020103.txt:131
            ./plos/pmed.0020117.txt:26
            ./plos/journal.pbio.0020353.txt:39
            ./plos/journal.pbio.0020347.txt:151
            ./plos/journal.pbio.0020420.txt:92
            ./plos/journal.pbio.0020346.txt:72
            ./plos/journal.pbio.0020187.txt:89
            ./plos/pmed.0020116.txt:25
            ./plos/pmed.0020102.txt:67
            ./plos/journal.pbio.0020150.txt:116
            ./plos/pmed.0020062.txt:81
            ./plos/pmed.0020274.txt:24
            ./plos/journal.pbio.0020232.txt:87
            ./plos/journal.pbio.0030021.txt:74
            ./plos/journal.pbio.0020224.txt:76
            ./plos/pmed.0020048.txt:9
            ./plos/pmed.0020060.txt:83
            ./plos/pmed.0020074.txt:22
            ./plos/journal.pbio.0020146.txt:146
            ./plos/pmed.0020114.txt:30
            ./plos/pmed.0010028.txt:186
            ./plos/journal.pbio.0020350.txt:134
            ./plos/journal.pbio.0020190.txt:109
            ./plos/pmed.0010029.txt:19
            ./plos/pmed.0020115.txt:24
            ./plos/journal.pbio.0020147.txt:62
            ./plos/pmed.0020075.txt:47
            ./plos/pmed.0020061.txt:113
            ./plos/pmed.0020210.txt:62
            ./plos/pmed.0020238.txt:30
            ./plos/journal.pbio.0030051.txt:82
            ./plos/journal.pbio.0020068.txt:98
            ./plos/journal.pbio.0020054.txt:131
            ./plos/journal.pbio.0020040.txt:52
            ./plos/pmed.0010066.txt:101
            ./plos/journal.pbio.0030131.txt:83
            ./plos/journal.pbio.0020337.txt:99
            ./plos/pmed.0020198.txt:27
            ./plos/pmed.0010067.txt:19
            ./plos/journal.pbio.0020121.txt:113
            ./plos/pmed.0020007.txt:58
            ./plos/journal.pbio.0030050.txt:100
            ./plos/pmed.0020239.txt:32
            ./plos/journal.pbio.0020241.txt:95
            ./plos/pmed.0020005.txt:62
            ./plos/journal.pbio.0020043.txt:155
            ./plos/pmed.0020039.txt:85
            ./plos/pmed.0010071.txt:42
            ./plos/journal.pbio.0030127.txt:131
            ./plos/pmed.0010058.txt:104
            ./plos/pmed.0010070.txt:26
            ./plos/pmed.0010064.txt:187
            ./plos/pmed.0020158.txt:41
            ./plos/journal.pbio.0020042.txt:79
            ./plos/journal.pbio.0020297.txt:79
            ./plos/pmed.0020206.txt:107
            ./plos/pmed.0020212.txt:92
            ./plos/pmed.0020216.txt:135
            ./plos/journal.pbio.0030094.txt:85
            ./plos/journal.pbio.0020046.txt:103
            ./plos/pmed.0020028.txt:12
            ./plos/journal.pbio.0020052.txt:92
            ./plos/pmed.0020148.txt:19
            ./plos/pmed.0020160.txt:123
            ./plos/pmed.0010048.txt:33
            ./plos/pmed.0010060.txt:88
            ./plos/journal.pbio.0030137.txt:149
            ./plos/journal.pbio.0030136.txt:88
            ./plos/pmed.0010061.txt:40
            ./plos/pmed.0010049.txt:21
            ./plos/pmed.0020161.txt:79
            ./plos/journal.pbio.0020127.txt:96
            ./plos/pmed.0020149.txt:22
            ./plos/journal.pbio.0020133.txt:73
            ./plos/pmed.0020015.txt:157
            ./plos/journal.pbio.0020053.txt:137
            ./plos/journal.pbio.0020047.txt:39
            ./plos/pmed.0020203.txt:29
            ./plos/journal.pbio.0030056.txt:102
            ./plos/pmed.0020201.txt:31
            ./plos/journal.pbio.0030097.txt:99
            ./plos/pmed.0020017.txt:53
            ./plos/journal.pbio.0020125.txt:77
            ./plos/journal.pbio.0020440.txt:155
            ./plos/pmed.0010062.txt:111
            ./plos/pmed.0020189.txt:19
            ./plos/pmed.0020162.txt:158
            ./plos/pmed.0020016.txt:161
            ./plos/pmed.0020002.txt:72
            ./plos/pmed.0020200.txt:26
            ./plos/pmed.0020231.txt:50
            ./plos/journal.pbio.0020263.txt:57
            ./plos/pmed.0020027.txt:11
            ./plos/pmed.0020033.txt:60
            ./plos/journal.pbio.0020101.txt:80
            ./plos/pmed.0010047.txt:30
            ./plos/journal.pbio.0030105.txt:55
            ./plos/journal.pbio.0020302.txt:108
            ./plos/pmed.0010046.txt:44
            ./plos/pmed.0010052.txt:92
            ./plos/pmed.0020191.txt:4
            ./plos/journal.pbio.0020100.txt:59
            ./plos/pmed.0020146.txt:27
            ./plos/journal.pbio.0020262.txt:60
            ./plos/journal.pbio.0030065.txt:93
            ./plos/journal.pbio.0020276.txt:82
            ./plos/pmed.0020232.txt:102
            ./plos/pmed.0020226.txt:4
            ./plos/pmed.0020024.txt:24
            ./plos/pmed.0020018.txt:210
            ./plos/pmed.0020144.txt:38
            ./plos/pmed.0020150.txt:21
            ./plos/journal.pbio.0020116.txt:94
            ./plos/pmed.0020187.txt:41
            ./plos/pmed.0010050.txt:21
            ./plos/pmed.0010051.txt:33
            ./plos/pmed.0020192.txt:3
            ./plos/pmed.0010045.txt:84
            ./plos/pmed.0020145.txt:16
            ./plos/pmed.0020019.txt:14
            ./plos/journal.pbio.0020063.txt:42
            ./plos/journal.pbio.0030076.txt:89
            ./plos/journal.pbio.0030062.txt:109
            ./plos/pmed.0020237.txt:27
            ./plos/journal.pbio.0020067.txt:83
            ./plos/pmed.0020009.txt:133
            ./plos/journal.pbio.0020073.txt:67
            ./plos/pmed.0020035.txt:39
            ./plos/pmed.0020021.txt:17
            ./plos/journal.pbio.0020113.txt:142
            ./plos/pmed.0020155.txt:56
            ./plos/pmed.0010069.txt:26
            ./plos/pmed.0010041.txt:47
            ./plos/pmed.0020182.txt:196
            ./plos/pmed.0020196.txt:20
            ./plos/journal.pbio.0020311.txt:96
            ./plos/journal.pbio.0030102.txt:113
            ./plos/journal.pbio.0020310.txt:99
            ./plos/pmed.0020197.txt:27
            ./plos/pmed.0010068.txt:13
            ./plos/pmed.0020140.txt:100
            ./plos/journal.pbio.0020112.txt:57
            ./plos/pmed.0020020.txt:24
            ./plos/pmed.0020034.txt:133
            ./plos/pmed.0020236.txt:38
            ./plos/journal.pbio.0020272.txt:61
            ./plos/pmed.0020208.txt:58
            ./plos/journal.pbio.0020064.txt:117
            ./plos/pmed.0020022.txt:22
            ./plos/pmed.0020036.txt:42
            ./plos/pmed.0010056.txt:81
            ./plos/pmed.0020195.txt:15
            ./plos/pmed.0010042.txt:78
            ./plos/pmed.0020181.txt:41
            ./plos/journal.pbio.0020306.txt:100
            ./plos/journal.pbio.0030129.txt:49
            ./plos/journal.pbio.0020307.txt:76
            ./plos/pmed.0020180.txt:45
            ./plos/pmed.0020194.txt:40
            ./plos/pmed.0020157.txt:10
            ./plos/journal.pbio.0020105.txt:50
            ./plos/pmed.0020023.txt:25
            ./plos/journal.pbio.0020071.txt:45
            ./plos/pmed.0020235.txt:34
            ./plos/journal.pbio.0020267.txt:145
            ./plos/pmed.0020209.txt:139
            ./plos/pmed.0020246.txt:230
            ./plos/journal.pbio.0020228.txt:99
            ./plos/journal.pbio.0020214.txt:103
            ./plos/pmed.0020050.txt:204
            ./plos/pmed.0020118.txt:48
            ./plos/pmed.0010030.txt:21
            ./plos/pmed.0010024.txt:23
            ./plos/journal.pbio.0020348.txt:92
            ./plos/journal.pbio.0020406.txt:163
            ./plos/pmed.0010025.txt:12
            ./plos/pmed.0020086.txt:12
            ./plos/pmed.0020045.txt:123
            ./plos/journal.pbio.0020215.txt:66
            ./plos/pmed.0020247.txt:82
            ./plos/pmed.0020047.txt:30
            ./plos/journal.pbio.0020001.txt:147
            ./plos/pmed.0020090.txt:25
            ./plos/journal.pbio.0020161.txt:168
            ./plos/journal.pbio.0020439.txt:208
            ./plos/journal.pbio.0020404.txt:113
            ./plos/pmed.0010026.txt:49
            ./plos/journal.pbio.0020148.txt:127
            ./plos/pmed.0020085.txt:14
            ./plos/pmed.0020091.txt:30
            ./plos/journal.pbio.0020028.txt:119
            ./plos/journal.pbio.0020216.txt:88
            ./plos/pmed.0020278.txt:13
            ./plos/pmed.0020268.txt:33
            ./plos/journal.pbio.0020206.txt:117
            ./plos/journal.pbio.0020010.txt:46
            ./plos/journal.pbio.0020164.txt:123
            ./plos/pmed.0010022.txt:40
            ./plos/pmed.0010036.txt:204
            ./plos/journal.pbio.0020400.txt:113
            ./plos/journal.pbio.0020401.txt:98
            ./plos/pmed.0010023.txt:26
            ./plos/pmed.0020123.txt:135
            ./plos/pmed.0020094.txt:20
            ./plos/journal.pbio.0020213.txt:136
            ./plos/pmed.0020257.txt:22
            ./plos/journal.pbio.0020013.txt:83
            ./plos/pmed.0020055.txt:38
            ./plos/pmed.0020082.txt:14
            ./plos/pmed.0010021.txt:86
            ./plos/pmed.0010034.txt:55
            ./plos/pmed.0010008.txt:124
            ./plos/pmed.0020120.txt:13
            ./plos/journal.pbio.0020172.txt:75
            ./plos/pmed.0020040.txt:76
            ./plos/pmed.0020068.txt:81
            ./plos/journal.pbio.0020012.txt:123
            ./plos/pmed.0020281.txt:20
            ./plos/pmed.0020242.txt:25
  
3. ## Command 3: `grep -i` (Found using `man grep`)
- Source Used: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**:
  
4. ## Command 4: `grep -v` (Found using `man grep`)
- **Source Used**: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**:


# Sources Used
1. “Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.
2. `man grep` Command (
