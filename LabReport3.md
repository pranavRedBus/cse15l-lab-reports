# Part 1 (`reversed()` in `Array Examples`)


## - A Failure-Inducing Input
```
      
      @Test
      public void testReversed() {
     
        int[] input1 = {1,2,3,4,5};
     
        assertArrayEquals(new int[]{5,4,3,2,1}, ArrayExamples.reversed(input1));
     
      }
```

## - A Working Input
```

      @Test
      public void testReversed() {
     
        int[] input1 = { };
     
        assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
     
      }
```

## - Symptom
-   Working Output
![ReverseWorksTest](ReverseWorksTest.png)

-   Failure Output
![ReverseFailure](ReverseFailure.png)


## - Bug
-   Before

```

    static int[] reversed(int[] arr) {

        int[] newArray = new int[arr.length];
    
        for(int i = 0; i < arr.length; i += 1) {
          arr[i] = newArray[arr.length - i - 1];
        }
        return arr;
    }
```

- After
```
    static int[] reversed(int[] arr) {
      
        int[] newArray = new int[arr.length];
    
        for(int i = 0; i < arr.length; i += 1) {
          newArray[arr.length - i - 1] = arr[i];
        }
      
        return newArray;
    }
```

- **Explanation of Fix:** 
  The fix above works as the original code's bug was that it didn't rigorously test the `reverse()` method at all, creating an empty array to feed into it but not a comprehensive, filled array. By making this switch, I ensure that when the code is passed in with a 5 element `int[]` array, it properly returns the reverse copy of that array, checking with the hand-checked reversed array in the test method. 

# Part 2 (Researching `grep`)
1. ## Command 1: `grep -l` (Found using `man grep`)
- **Source Used**: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**: `grep -l` lists the names of the files, rather than the direct lines from the files, which contain the specified string. In this case, grep -r recursively searches the `technical` directory (current directory) for matches to *''base pair''*, and `-l` forces the output to list the names of the files, rather than each line in the file that contains the phrase. 

```
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
```

- **Example 2**: `grep -l` lists the names of the files, rather than the direct lines from the files, which contain the specified string. In this case, grep -r recursively searches the `plos` directory for matches to *''base pair''*, and `-l` forces the output to list the names of the files, rather than each line in the file that contains the phrase. 

```
      pranavrb@Pranavs-MacBook-Pro technical % grep -r  -l "base pair" ./plos  
            ./plos/journal.pbio.0020223.txt
            ./plos/journal.pbio.0020190.txt
```

2. ## Command 2: `grep -c` (Found using `man grep`)
- **Source Used**: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**: `grep -c` lists how many lines in the file contain the phrase. In this case, grep -c is given the file `biomed/rr74.txt`, and it returns 102 because that is how many lines in the file contain the phrase "the" as passed in.

```
      pranavrb@Pranavs-MacBook-Pro technical % grep -c  "the" ./biomed/rr74.txt
            102
```

- **Example 2**: `grep -c` lists how many lines in the file contain the phrase. In this case, `grep -c` is paired with `-r` (which recursively searches through directories and provides individuals files for `grep`) and given the directory `./plos` as the argument. `grep -c` in this command lists the number of lines in each file that contains the phrase.

```
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
```
  
3. ## Command 3: `grep -v` (Found using `man grep`)
- **Source Used**: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**: `grep -v` lists the lines of the file that do NOT contain the specified phrase, the exact opposite of what `grep` innately does. Combined with `grep -r`,  This command is executed recursively for all files in the specified directories and its further nested directories as well, though since only a file was given, only that file's content is checked and printed.

```
      pranavrb@Pranavs-MacBook-Pro technical % grep  -r -v  "a" ./biomed/1471-2164-2-4.txt
            ./biomed/1471-2164-2-4.txt:
            ./biomed/1471-2164-2-4.txt:  
            ./biomed/1471-2164-2-4.txt:    
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:        Results
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          the OCP is 20-30 bp in length, while the 3'
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          on genomic DNA.
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          different SNPs representing five of the six possible
            ./biomed/1471-2164-2-4.txt:          high throughput method of genotyping.
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          OCPs for the SNP G1822A.
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:        Discussion
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:        Conclusions
            ./biomed/1471-2164-2-4.txt:        Corp.
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          Oligonucleotides
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          Elmer).
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          Genomic DNA
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          Tris-HCl (pH 8.3), 25 mM KCl, 10 mM MgCl 
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          mM Tris-HCl (pH 8.8), 10 mM KCl, 10 mM (NH 
            ./biomed/1471-2164-2-4.txt:          4 ) 
            ./biomed/1471-2164-2-4.txt:          2 SO 
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:          Buffer supplied by Epicentre Technologies: 20 mM Tris-HCl
            ./biomed/1471-2164-2-4.txt:          (following Life Technologies suggested protocol for T4
            ./biomed/1471-2164-2-4.txt:          8% PAGE sequencing gel.
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:        
            ./biomed/1471-2164-2-4.txt:      
            ./biomed/1471-2164-2-4.txt:    
            ./biomed/1471-2164-2-4.txt:
```

- **Example 2**: `grep -v` lists the lines of the file that do NOT contain the specified phrase, the exact opposite of what `grep` innately does. Given the file `./biomed/1471-2164-2-4.txt` and phrase *"the"*, it printed out all the lines in the file not containing the phrase.

```
      pranavrb@Pranavs-MacBook-Pro technical % grep  -v  "the" ./biomed/1471-2164-2-4.txt
    
        Background
        Sequencing studies of human transcriptomes and genomes
        have identified hundreds of thousands of single nucleotide
        variation [ 1 ] . Human SNPs are being assembled into
        extremely high-density genetic maps that are anticipated to
        Broad availability of SNPs for candidate genes will enhance
        pharmacogenomic and complex trait association studies.
        make possible genome-wide association studies for complex
        traits that bypass shortcomings of current genetic linkage
        analyses [ 3 4 ] .
        The emerging era of multiplexed SNP-based genetic
        analysis has underscored a need for simple and accurate
        genotyping methods that can accommodate thousands of loci
        with economy of cost and consumption of sample DNA. In
        general, current methods require pre-amplification of
        genomic DNA, typically by Polymerase Chain Reaction (PCR),
        followed by SNP genotyping with an allele discrimination
        method, such as DNA cleavage, ligation, single base
        extension or hybridization [ 5 ] . Current methods are
        sample DNA, or lack of scalability.
        Recently a new method for SNP detection from genomic DNA
        based on DNA ligase-mediated single nucleotide
        discrimination and signal amplification by Rolling Circle
        Amplification (RCA) has been described [ 6 7 8 9 10 ] . An
        circularization. In this manner, single base selectivity is
        exponential RCA (ERCA) reaction involving an exonuclease
        (-) DNA polymerase with strand-displacement activity and
        12-fold, allowing for direct SNP genotyping from small
        quantities of DNA target [ 6 11 12 ] .
        We describe here a simple, scalable assay for SNP
        genotyping directly from human genomic DNA that uses a
        96-well plate format and fluorescent primers called
        Amplifluors™ [ 13 14 15 12 16 ] . Ten different SNPs have
        been characterized, each for DNA samples from 192 different
        individuals, using this reporter assay system. We also
      
      
        Results
        
          Experimental strategy
          Two OCPs were designed for each SNP screened, one
          it can be circularized by DNA ligase (Fig. 1). The OCPs
          were ∼ 90 nucleotides in length, and are designed such
          allele-specific OCPs. The 5' target-specific region of
          specificity of circularization is dependent upon two
          correctly base paired ends.
          template for an exponential, or hyperbranching, RCA
          backbone, provides a binding site for a complementary
          primer (P1). In addition to P1, a reverse primer (P2) is
          also present to achieve amplification with exponential
          kinetics (Fig. 1). P1 is an "Amplifluor™"-primer, with a
          5' hairpin and loop structure with a fluorophore and
          The two allele-specific OCPs have different backbone
          P1s have an internal DABCYL quencher. Amplifluor primers
          proximity, preventing fluorescence. Incorporation of
          resulting in increased fluorescence. Two different
          partly target- and partly backbone-specific,
          end to reduce primer-dimer formation (unpublished
          data).
        
        
          have excellent discrimination between a matched and
          mismatched 3' terminal nucleotide [ 17 ] . In order to
          was analyzed using 5' 32P-labeled OCP. The
          mutation. An electrophoretic mobility shift for
          circularized OCP allowed quantification of ligation
          kinetics. Use of 40 nM OCP and 100 nM oligonucleotide
          target allowed sufficient signal for detection without
          (Fig. 2a). For mismatched OCP, less than 1% was ligated
          after 6 hours (Fig. 2b). The ability of Ampligase to
          discriminate against a mismatch was measured by
          comparison of initial ligation rates. Allele
          Discrimination = (percent match ligation/percent mismatch
          ligation) (time 
          mismatch /time 
          match ). Ligation of matched OCP
          occurred at a 100,000-fold greater rate than for
          mismatched OCP. Greater temperature and shorter 3' OCP
          arm length both tended to give increased allele
          discrimination (Fig. 3). The T 
          and mismatched 3' arms. Presumably, increasing reaction
          arm.
        
        
          estimated 100-30,000 OCPs are circularized by ligation
          gel-purified to remove any linear DNA. A known number of
          direct analysis of ERCA signal amplification. The circles
          oligonucleotide target (Table I). A 10-fold serial
          assay is capable of detecting < 10 molecules of
          circular template (Fig. 4a). The time at which
          fluorescent signal is first detected (C 
          potential of ERCA and that it is capable of detecting and
          on genomic DNA.
        
        
          SNP genotyping on human genomic DNA
          The G1822A SNP on chromosome 13q32 was used for
          restriction endonuclease Alu I and assayed in two
          specific OCP. Reactions contained 0.5 pM OCP, and 100 ng
          of approximately 30,000. OCP ligation was performed with
          Ampligase for 20 min at 60°C, approximately 15°C above
          hybridizes to its target in a stable manner, and SNP
          allele (Fig. 5a, center panel) a fluorescence signal was
          heterozygous, a fluorescence signal was observed with
          both OCP/primer combinations (Fig. 5a, lower panel). When
          agarose gel, an ERCA product ladder was observed only for
          (Fig 5b). ERCA reactions produce a characteristic ladder
        
        
          individuals
          demonstrated on two sets of human genomic DNA samples,
          each containing DNA from 96 different individuals. Ten
          types of single nucleotide substitutions were assayed
          determined by restriction fragment length polymorphism or
          extension method. The SNP assay gave correct genotypes an
          accuracy was above 99% (data not shown). A scatter plot
          The protocol uses a microtiter plate format providing a
          high throughput method of genotyping.
        
        
          Single-tube assay for SNP genotyping using a low
          copy number of targets
          The above experiments involved a two-tube assay with
          100 ng of genomic DNA and one OCP/P2 combination per
          tube. Therefore, a total of 200 ng genomic DNA was used
          accurately detect a SNP from a small amount of genomic
          DNA. Previously, it was shown that 20 ng of genomic DNA,
          signal amplification reaction (SISAR) [ 18 ] . In order
          SNPs, 1 ng of genomic DNA, equivalent to ∼ 300 copies of
          The method was also simplified so that instead of one
          for both OCPs was used. Both OCP systems could be
          OCP. The P2 for one allele could only effectively prime
          specificity was achieved by two allele-specific
          Amplifluor primers (P2-1822C-TET and P2-1822T-FAM). This
          assay detected and differentiated all three possible
          signal observed was slightly higher than that obtained
          with 100 ng genomic DNA in a two-tube system, with a
          signal/noise ratio of 5:1. However, correct SNP
          genotyping was observed with 48 different human genomic
          DNA samples (data not shown).
        
      
      
        Discussion
        We have demonstrated a solution-based, efficient,
        homogeneous and robust assay for genotyping SNPs directly
        from human genomic DNA utilizing ligation of open circle
        amplification reaction) in a 96-well format. Specificity of
        ligation. Single nucleotide discrimination is achieved at
        ligase, Ampligase, which has a high affinity for a
        [ 17 ] . We were able to enhance allele discrimination at
        ligase. It has been previously reported that 3'-T/G and 3'
        G/T mismatches are not good substrates for single
        nucleotide discrimination [ 17 ] . However, we found that
        was efficient for allele discrimination. The ability of
        involved is an important advantage over assays based on
        primer extension such as PCR.
        results in small circular DNA molecules topologically
        of 10 12-fold signal amplification [ 6 ] , similar to that
        genetic analysis and quantitation. However, PCR involves
        risk of amplicon cross-contamination. Even though this
        high-throughput analysis. Since ERCA is a signal (circle)
        strategy can be easily adapted for a simple fluorescence
        plate reader coupled to an adjustable heating block. These
        properties make it an ideal system for high-throughput
        analysis.
        The assay was tested for 10 SNPS on two sets of 96
        different DNA samples (Table II). Results were compared to
        nucleotide sequencing reactions. The assay had an average
        genotyping accuracy of 93% when samples were screened
        being called heterozygous, i.e., an amplification signal
        was observed with both sets of OCP/primer combinations. A
        DNA sample homozygous for one allele was never genotyped as
        fluorescence signal.
        accuracy of SNP genotyping. In addition, reagents that have
        been shown to reduce primer-dimer formation in PCR will be
        concentration needs to be determined before screening.
        Excess OCP concentrations result in an increase in
        accuracy rate of genotyping. Potentially, un-ligated OCP
        can act as template or primer giving rise to a low level of
        signal. We are currently developing a modified OCP design
        hairpin-loop structure and opens up only to anneal to it
        target sequence (O. Alsmadi, unpublished). As with
        molecular beacons, this may also improve target specificity
        [ 19 20 ] . Any unused OCP is self primed and extended to
        form an inert double stranded molecule, thus eliminating
        OCP as a source for non-specific amplification. Initial
        experiments with this design have been encouraging.
      
      
        Conclusions
        We have described a solution-based SNP genotyping assay
        that is simple, sensitive and robust and can be easily
        formatted to high-throughput analysis of single nucleotide
        polymorphisms and mutation detection directly from human
        genomic DNA. The SNP genotyping assay uses a simple,
        homogeneous, fluorescence readout and can be carried out on
        inexpensive instruments already available in many academic
        and industrial laboratories.
        Amplifluor is a trademark of Intergen Company.
        Ampligase is a trademark of Epicentre Technologies
        Corp.
      
      
        Materials and methods
        
          Oligonucleotides
          oligonucleotides were obtained from Integrated DNA
          Technologies, Inc. (Coralville, IA). Abasic and
          by HPLC. The two Amplifluors are labeled with a
          differently colored fluorophore: fluorescein (FAM) and
          tetrachloro-6-carboxyfluorescein (TET) and contain an
          internal nonfluorescent quencher DABCYL.
        
        
          Instrumentation
          DNA denaturation, annealing and ligation reactions
          were carried out in an Eppendorf Master Cycler (Eppendorf
          Scientific, Germany). ERCA reactions were performed in
          Elmer).
        
        
          Genomic DNA
          Genomic DNA samples were obtained from (a) National
          Institute of Mental Health (NIMH) Center for Genetic
          Studies, Rutgers University Cell and DNA Repository,
          Piscataway, NJ and (b) Coriell Cell Repository (HD 100
          ligation reaction.
        
        
          DNA annealing and ligation
          The reactions were set up in 96-well MicroAmp Optical
          plates (Perkin Elmer) in a 10 μl reaction volume
          containing 1 U Ampligase (Epicentre Technologies), 20 mM
          Tris-HCl (pH 8.3), 25 mM KCl, 10 mM MgCl 
          2 , 0.5 mM NAD, and 0.01% Triton
          ®X-100. Standard reactions contained 0.5 pM OCP and 100
          ng of Alu I digested genomic DNA. DNA was denatured by
          annealing and ligation at 60°C for 20 min.
        
        
          ERCA reaction
          reaction. The ERCA mix contained 5% tetramethyl ammonium
          primers, 8 u of Bst polymerase (New England Biolabs, MA),
          and 1X modified ThermoPol reaction buffer containing 20
          mM Tris-HCl (pH 8.8), 10 mM KCl, 10 mM (NH 
          4 ) 
          2 SO 
          4 and 0.1% Triton X-100.
        
        
          All ligation reactions were in 1x Ampligase Reaction
          Buffer supplied by Epicentre Technologies: 20 mM Tris-HCl
          (pH8.3 at 25°C), 25 mM KCl, 10 mM MgCl 
          2 , 0.5 mM NAD +, and 0.01% Triton
          (following Life Technologies suggested protocol for T4
          PNK). 40 nM CFTR M1101K12 OCP (Table I) was annealed to
          100 nM oligo target, at 95°C, 2 min, and slow cooled to
          room temperature. Reactions were started by adding
          Ampligase at 0.2 units/μl final concentration in a
          reaction volume of 0.1 ml. Reactions time points were
          taken at 15, 30, and 60 sec for matched OCP and 1, 2, 4,
          and 6 hours for mismatched OCP. 3.5 μl was resolved on an
          8% PAGE sequencing gel.
        
        
          OCP 3' arm length and ligation reaction
          temperature
          OCP were designed with 12, 15, 20, or 23 nt 3' arms
          (Table I). All components except Ampligase were
          63°C) for 20 min to allow OCP annealing to come to
          equilibrium. Reactions were started by adding Ampligase
          at 0.2 units/μl final concentration and a reaction volume
          reaction temperatures indicated. Reactions were stopped
          at 1 min for matched OCP and 4 hours for mismatched OCP
          by digestion with 0.75 units/μl Exonuclease I and 1.25
          units/μl T7 gene 6 exonuclease (Amersham Pharmacia
          points. The digestion removes all but circular DNA. 3.5
          μl was resolved on an 8% PAGE sequencing gel.
```
  
4. ## Command 4: `grep -L` (Found using `man grep`)
- **Source Used**: *“Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.*
- **Example 1**: `grep -L` lists the names of the files, rather than the direct lines from the files, which **DO NOT** contain the specified string. In this case, grep -r recursively searches the `biomed` directory for matches to *''base''*, and `-L` forces the output to list the names of the files that do not contain the phrase at all. It is functionally opposite to `grep -l`.

```
      pranavrb@Pranavs-MacBook-Pro technical % grep  -r -L  "base" ./biomed
            ./biomed/bcr620.txt
            ./biomed/1471-2091-2-11.txt
            ./biomed/1471-2202-4-12.txt
            ./biomed/rr73.txt
            ./biomed/1471-2202-2-8.txt
            ./biomed/1471-2350-4-2.txt
            ./biomed/1476-0711-2-7.txt
            ./biomed/1471-2121-3-13.txt
            ./biomed/ar118.txt
            ./biomed/1471-2210-1-10.txt
            ./biomed/1476-4598-2-20.txt
            ./biomed/1472-6769-1-4.txt
            ./biomed/cc4.txt
            ./biomed/1471-2121-3-12.txt
            ./biomed/bcr568.txt
            ./biomed/ar93.txt
            ./biomed/cc367.txt
            ./biomed/rr74.txt
            ./biomed/1471-2210-1-8.txt
            ./biomed/1471-2091-3-8.txt
            ./biomed/1471-230X-2-21.txt
            ./biomed/ar120.txt
            ./biomed/1471-2407-1-19.txt
            ./biomed/rr171.txt
            ./biomed/1471-2172-3-1.txt
            ./biomed/1471-2415-3-3.txt
            ./biomed/1472-6769-1-3.txt
            ./biomed/1471-2202-4-16.txt
            ./biomed/1471-2180-2-26.txt
            ./biomed/ar321.txt
            ./biomed/1471-230X-2-23.txt
            ./biomed/rr172.txt
            ./biomed/1472-6785-1-5.txt
            ./biomed/1471-2172-4-1.txt
            ./biomed/ar795.txt
            ./biomed/ar408.txt
            ./biomed/1471-230X-1-5.txt
            ./biomed/1471-2172-3-12.txt
            ./biomed/1471-213X-1-1.txt
            ./biomed/1471-2202-2-10.txt
            ./biomed/1471-2172-4-2.txt
            ./biomed/1471-2091-3-30.txt
            ./biomed/1471-2172-2-4.txt
            ./biomed/1471-2121-2-18.txt
            ./biomed/ar422.txt
            ./biomed/1475-925X-2-12.txt
            ./biomed/cc1882.txt
            ./biomed/1471-2180-3-9.txt
            ./biomed/1471-2091-3-31.txt
            ./biomed/1471-213X-1-2.txt
            ./biomed/1471-2202-3-8.txt
            ./biomed/1477-7827-1-48.txt
            ./biomed/1471-213X-3-4.txt
            ./biomed/1471-2490-3-2.txt
            ./biomed/ar383.txt
            ./biomed/ar745.txt
            ./biomed/1471-213X-3-7.txt
            ./biomed/1471-2180-3-11.txt
            ./biomed/1471-2202-2-14.txt
            ./biomed/cc713.txt
            ./biomed/1471-2407-2-15.txt
            ./biomed/1471-2296-3-18.txt
            ./biomed/ar140.txt
            ./biomed/1477-7827-1-43.txt
            ./biomed/1471-2202-1-1.txt
            ./biomed/1471-2210-2-6.txt
            ./biomed/1476-4598-2-3.txt
            ./biomed/1471-2121-2-12.txt
            ./biomed/1475-925X-2-6.txt
            ./biomed/ar429.txt
            ./biomed/1472-6793-3-5.txt
            ./biomed/1471-2199-3-11.txt
            ./biomed/1472-6750-2-10.txt
            ./biomed/1471-2210-2-5.txt
            ./biomed/gb-2001-3-1-research0005.txt
            ./biomed/1471-2334-2-26.txt
            ./biomed/1476-5918-1-2.txt
            ./biomed/1471-2407-2-33.txt
            ./biomed/1471-2121-3-6.txt
            ./biomed/1471-2334-2-27.txt
            ./biomed/1471-2199-3-10.txt
            ./biomed/ar407.txt
            ./biomed/1475-2867-3-2.txt
            ./biomed/1471-2091-3-15.txt
            ./biomed/1471-2202-3-4.txt
            ./biomed/cc1495.txt
            ./biomed/1475-9268-1-2.txt
            ./biomed/ar799.txt
            ./biomed/1471-230X-1-8.txt
            ./biomed/ar149.txt
            ./biomed/cc350.txt
            ./biomed/1471-2199-2-2.txt
            ./biomed/1471-213X-2-8.txt
            ./biomed/1471-2369-3-1.txt
            ./biomed/1471-2121-3-18.txt
            ./biomed/1471-2121-2-6.txt
            ./biomed/1475-2891-1-2.txt
            ./biomed/1471-2334-3-11.txt
            ./biomed/1471-2202-2-3.txt
            ./biomed/1471-2210-1-4.txt
            ./biomed/1471-2121-4-2.txt
            ./biomed/cc1547.txt
            ./biomed/1476-4598-2-28.txt
            ./biomed/1477-7827-1-36.txt
            ./biomed/1471-213X-1-13.txt
            ./biomed/1471-2199-2-4.txt
            ./biomed/1471-2474-3-23.txt
            ./biomed/1471-2202-2-6.txt
            ./biomed/1475-2867-2-15.txt
            ./biomed/1471-2164-2-6.txt
            ./biomed/1471-2334-1-10.txt
            ./biomed/1471-2121-3-22.txt
            ./biomed/rr191.txt
            ./biomed/1471-2148-1-6.txt
            ./biomed/1471-2202-4-3.txt
            ./biomed/1471-230X-2-17.txt
            ./biomed/1477-5956-1-1.txt
            ./biomed/ar328.txt
            ./biomed/1471-2121-4-5.txt
            ./biomed/1471-2202-3-17.txt
            ./biomed/1478-1336-1-3.txt
            ./biomed/1471-2210-1-3.txt
            ./biomed/1471-2334-1-13.txt
            ./biomed/1471-2172-3-9.txt
```

- **Example 2**:  `grep -L` lists the names of the files, rather than the direct lines from the files, which **DO NOT** contain the specified string. In this case, grep -r recursively searches the `plos` directory for matches to *''base pair''*, and `-L` forces the output to list the names of the files that do not contain the phrase at all.

```
      pranavrb@Pranavs-MacBook-Pro technical % grep -r  -L "base pair" ./plos 
            ./plos/pmed.0020273.txt
            ./plos/journal.pbio.0030032.txt
            ./plos/pmed.0020065.txt
            ./plos/pmed.0020071.txt
            ./plos/pmed.0020059.txt
            ./plos/pmed.0010039.txt
            ./plos/journal.pbio.0020354.txt
            ./plos/pmed.0010010.txt
            ./plos/journal.pbio.0020156.txt
            ./plos/pmed.0020104.txt
            ./plos/pmed.0020272.txt
            ./plos/pmed.0020258.txt
            ./plos/pmed.0020099.txt
            ./plos/journal.pbio.0020140.txt
            ./plos/journal.pbio.0020183.txt
            ./plos/journal.pbio.0020430.txt
            ./plos/journal.pbio.0020394.txt
            ./plos/journal.pbio.0020431.txt
            ./plos/journal.pbio.0020419.txt
            ./plos/pmed.0010013.txt
            ./plos/pmed.0020113.txt
            ./plos/journal.pbio.0020169.txt
            ./plos/pmed.0020098.txt
            ./plos/journal.pbio.0020035.txt
            ./plos/pmed.0020067.txt
            ./plos/pmed.0020073.txt
            ./plos/journal.pbio.0030024.txt
            ./plos/pmed.0020249.txt
            ./plos/pmed.0020275.txt
            ./plos/journal.pbio.0020019.txt
            ./plos/pmed.0020088.txt
            ./plos/journal.pbio.0020145.txt
            ./plos/pmed.0020103.txt
            ./plos/pmed.0020117.txt
            ./plos/journal.pbio.0020353.txt
            ./plos/journal.pbio.0020347.txt
            ./plos/journal.pbio.0020420.txt
            ./plos/journal.pbio.0020346.txt
            ./plos/journal.pbio.0020187.txt
            ./plos/pmed.0020116.txt
            ./plos/pmed.0020102.txt
            ./plos/journal.pbio.0020150.txt
            ./plos/pmed.0020062.txt
            ./plos/pmed.0020274.txt
            ./plos/journal.pbio.0020232.txt
            ./plos/journal.pbio.0030021.txt
            ./plos/journal.pbio.0020224.txt
            ./plos/pmed.0020048.txt
            ./plos/pmed.0020060.txt
            ./plos/pmed.0020074.txt
            ./plos/journal.pbio.0020146.txt
            ./plos/pmed.0020114.txt
            ./plos/pmed.0010028.txt
            ./plos/journal.pbio.0020350.txt
            ./plos/pmed.0010029.txt
            ./plos/pmed.0020115.txt
            ./plos/journal.pbio.0020147.txt
            ./plos/pmed.0020075.txt
            ./plos/pmed.0020061.txt
            ./plos/pmed.0020210.txt
            ./plos/pmed.0020238.txt
            ./plos/journal.pbio.0030051.txt
            ./plos/journal.pbio.0020068.txt
            ./plos/journal.pbio.0020054.txt
            ./plos/journal.pbio.0020040.txt
            ./plos/pmed.0010066.txt
            ./plos/journal.pbio.0030131.txt
            ./plos/journal.pbio.0020337.txt
            ./plos/pmed.0020198.txt
            ./plos/pmed.0010067.txt
            ./plos/journal.pbio.0020121.txt
            ./plos/pmed.0020007.txt
            ./plos/journal.pbio.0030050.txt
            ./plos/pmed.0020239.txt
            ./plos/journal.pbio.0020241.txt
            ./plos/pmed.0020005.txt
            ./plos/journal.pbio.0020043.txt
            ./plos/pmed.0020039.txt
            ./plos/pmed.0010071.txt
            ./plos/journal.pbio.0030127.txt
            ./plos/pmed.0010058.txt
            ./plos/pmed.0010070.txt
            ./plos/pmed.0010064.txt
            ./plos/pmed.0020158.txt
            ./plos/journal.pbio.0020042.txt
            ./plos/journal.pbio.0020297.txt
            ./plos/pmed.0020206.txt
            ./plos/pmed.0020212.txt
            ./plos/pmed.0020216.txt
            ./plos/journal.pbio.0030094.txt
            ./plos/journal.pbio.0020046.txt
            ./plos/pmed.0020028.txt
            ./plos/journal.pbio.0020052.txt
            ./plos/pmed.0020148.txt
            ./plos/pmed.0020160.txt
            ./plos/pmed.0010048.txt
            ./plos/pmed.0010060.txt
            ./plos/journal.pbio.0030137.txt
            ./plos/journal.pbio.0030136.txt
            ./plos/pmed.0010061.txt
            ./plos/pmed.0010049.txt
            ./plos/pmed.0020161.txt
            ./plos/journal.pbio.0020127.txt
            ./plos/pmed.0020149.txt
            ./plos/journal.pbio.0020133.txt
            ./plos/pmed.0020015.txt
            ./plos/journal.pbio.0020053.txt
            ./plos/journal.pbio.0020047.txt
            ./plos/pmed.0020203.txt
            ./plos/journal.pbio.0030056.txt
            ./plos/pmed.0020201.txt
            ./plos/journal.pbio.0030097.txt
            ./plos/pmed.0020017.txt
            ./plos/journal.pbio.0020125.txt
            ./plos/journal.pbio.0020440.txt
            ./plos/pmed.0010062.txt
            ./plos/pmed.0020189.txt
            ./plos/pmed.0020162.txt
            ./plos/pmed.0020016.txt
            ./plos/pmed.0020002.txt
            ./plos/pmed.0020200.txt
            ./plos/pmed.0020231.txt
            ./plos/journal.pbio.0020263.txt
            ./plos/pmed.0020027.txt
            ./plos/pmed.0020033.txt
            ./plos/journal.pbio.0020101.txt
            ./plos/pmed.0010047.txt
            ./plos/journal.pbio.0030105.txt
            ./plos/journal.pbio.0020302.txt
            ./plos/pmed.0010046.txt
            ./plos/pmed.0010052.txt
            ./plos/pmed.0020191.txt
            ./plos/journal.pbio.0020100.txt
            ./plos/pmed.0020146.txt
            ./plos/journal.pbio.0020262.txt
            ./plos/journal.pbio.0030065.txt
            ./plos/journal.pbio.0020276.txt
            ./plos/pmed.0020232.txt
            ./plos/pmed.0020226.txt
            ./plos/pmed.0020024.txt
            ./plos/pmed.0020018.txt
            ./plos/pmed.0020144.txt
            ./plos/pmed.0020150.txt
            ./plos/journal.pbio.0020116.txt
            ./plos/pmed.0020187.txt
            ./plos/pmed.0010050.txt
            ./plos/pmed.0010051.txt
            ./plos/pmed.0020192.txt
            ./plos/pmed.0010045.txt
            ./plos/pmed.0020145.txt
            ./plos/pmed.0020019.txt
            ./plos/journal.pbio.0020063.txt
            ./plos/journal.pbio.0030076.txt
            ./plos/journal.pbio.0030062.txt
            ./plos/pmed.0020237.txt
            ./plos/journal.pbio.0020067.txt
            ./plos/pmed.0020009.txt
            ./plos/journal.pbio.0020073.txt
            ./plos/pmed.0020035.txt
            ./plos/pmed.0020021.txt
            ./plos/journal.pbio.0020113.txt
            ./plos/pmed.0020155.txt
            ./plos/pmed.0010069.txt
            ./plos/pmed.0010041.txt
            ./plos/pmed.0020182.txt
            ./plos/pmed.0020196.txt
            ./plos/journal.pbio.0020311.txt
            ./plos/journal.pbio.0030102.txt
            ./plos/journal.pbio.0020310.txt
            ./plos/pmed.0020197.txt
            ./plos/pmed.0010068.txt
            ./plos/pmed.0020140.txt
            ./plos/journal.pbio.0020112.txt
            ./plos/pmed.0020020.txt
            ./plos/pmed.0020034.txt
            ./plos/pmed.0020236.txt
            ./plos/journal.pbio.0020272.txt
            ./plos/pmed.0020208.txt
            ./plos/journal.pbio.0020064.txt
            ./plos/pmed.0020022.txt
            ./plos/pmed.0020036.txt
            ./plos/pmed.0010056.txt
            ./plos/pmed.0020195.txt
            ./plos/pmed.0010042.txt
            ./plos/pmed.0020181.txt
            ./plos/journal.pbio.0020306.txt
            ./plos/journal.pbio.0030129.txt
            ./plos/journal.pbio.0020307.txt
            ./plos/pmed.0020180.txt
            ./plos/pmed.0020194.txt
            ./plos/pmed.0020157.txt
            ./plos/journal.pbio.0020105.txt
            ./plos/pmed.0020023.txt
            ./plos/journal.pbio.0020071.txt
            ./plos/pmed.0020235.txt
            ./plos/journal.pbio.0020267.txt
            ./plos/pmed.0020209.txt
            ./plos/pmed.0020246.txt
            ./plos/journal.pbio.0020228.txt
            ./plos/journal.pbio.0020214.txt
            ./plos/pmed.0020050.txt
            ./plos/pmed.0020118.txt
            ./plos/pmed.0010030.txt
            ./plos/pmed.0010024.txt
            ./plos/journal.pbio.0020348.txt
            ./plos/journal.pbio.0020406.txt
            ./plos/pmed.0010025.txt
            ./plos/pmed.0020086.txt
            ./plos/pmed.0020045.txt
            ./plos/journal.pbio.0020215.txt
            ./plos/pmed.0020247.txt
            ./plos/pmed.0020047.txt
            ./plos/journal.pbio.0020001.txt
            ./plos/pmed.0020090.txt
            ./plos/journal.pbio.0020161.txt
            ./plos/journal.pbio.0020439.txt
            ./plos/journal.pbio.0020404.txt
            ./plos/pmed.0010026.txt
            ./plos/journal.pbio.0020148.txt
            ./plos/pmed.0020085.txt
            ./plos/pmed.0020091.txt
            ./plos/journal.pbio.0020028.txt
            ./plos/journal.pbio.0020216.txt
            ./plos/pmed.0020278.txt
            ./plos/pmed.0020268.txt
            ./plos/journal.pbio.0020206.txt
            ./plos/journal.pbio.0020010.txt
            ./plos/journal.pbio.0020164.txt
            ./plos/pmed.0010022.txt
            ./plos/pmed.0010036.txt
            ./plos/journal.pbio.0020400.txt
            ./plos/journal.pbio.0020401.txt
            ./plos/pmed.0010023.txt
            ./plos/pmed.0020123.txt
            ./plos/pmed.0020094.txt
            ./plos/journal.pbio.0020213.txt
            ./plos/pmed.0020257.txt
            ./plos/journal.pbio.0020013.txt
            ./plos/pmed.0020055.txt
            ./plos/pmed.0020082.txt
            ./plos/pmed.0010021.txt
            ./plos/pmed.0010034.txt
            ./plos/pmed.0010008.txt
            ./plos/pmed.0020120.txt
            ./plos/journal.pbio.0020172.txt
            ./plos/pmed.0020040.txt
            ./plos/pmed.0020068.txt
            ./plos/journal.pbio.0020012.txt
            ./plos/pmed.0020281.txt
            ./plos/pmed.0020242.txt
```

# Sources Used
1. “Grep ¶.” GNU Grep 3.11, www.gnu.org/software/grep/manual/grep.html. Accessed 13 Feb. 2024.
2. `man grep` Command
