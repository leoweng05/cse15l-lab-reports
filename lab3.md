# Lab Report 3 - Bugs and Commands (Week 5)

## Part 1 - Bugs

Failure Inducing Input:
```	
@Test 
public void testReverseInPlace() {
    int[] input2 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{3, 2, 1}, input2);
} 
 ```

 Input that doesn't induce failure: 
 ```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
}
 ```

Symptoms:
* For Failure Inducing Input: ![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/07387763-c19c-4cd1-a850-a01ea9122964)
* For Input that doesn't induce failure: ![image](https://github.com/leoweng05/cse15l-lab-reports/assets/62259208/f58603ae-3717-4f26-83c7-89321dfec4be)

Bug:
* Before:
```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
* After:
```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] tempArr = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      tempArr[i] = arr[arr.length - i - 1];
    }
    for (int i 0; i < arr.length; i++){
      arr[i] = tempArr[i];
    }
  }
  ```
The reason why there was a bug was that the array was overwriting its values at the same time it was reading through them. This logic flaw only reverses the first half of the array, leaving the second half as it already is (because the first half was switched to be the mirror of the original second half, so mirroring that again would just leave the original second half). The fix accounts for this by reading through the array values but storing them in a temporary array, so the danger of overriding values would not occur. Then, it copies over the reversed values from the temp array to the original array, correctly leaving a fully reversed array. 

## Part 2 - Researching Commands

Command of choice - `find`

Options and Examples: 
1. `-not`

First Example:
```
$ find ./technical -not -name "*.txt"
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos
```
This command finds everything in the `technical` directory that is not a text file. This command could be useful to filter out certain file types, whether it's `.txt` or `.java` or anything.

Second Example:
```
$ find ./technical -not -user leowe
```
This command finds everything in the `technical` directory that is not owned by user `leowe`, which is my system. It could be useful to look for any files that I don't own, which can help with file security.

   * source used: https://snapshooter.com/learn/linux/find#basic-syntax


2. `-iname`

First Example:
```
$ find ./technical -iname "cohenetal_comparison.txt"                                                                                                
./technical/government/Post_Rate_Comm/Cohenetal_comparison.txt
```
This command finds the file named `Cohenetal_comparison.txt` even though the input is not capitalized correctly. This could be useful to look for specific file names if you aren't sure if it's capitalized or not because the `-iname` operator ignores case when looking for names.

Second Example:
```
$ find ./technical -iname "*cohenetal*"
./technical/government/Post_Rate_Comm/Cohenetal_comparison.txt
./technical/government/Post_Rate_Comm/Cohenetal_Cost_Function.txt
./technical/government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
./technical/government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt 
./technical/government/Post_Rate_Comm/Cohenetal_RuralDelivery.txt
./technical/government/Post_Rate_Comm/Cohenetal_Scale.txt
```
This command finds all files containing "cohenetal" in the file name regardless of capitalization. Similar to the first example, instead of specific file names, you can look for keywords in file names and ignore case, which is especially useful for large databases that may store files of varying capitalization. 
   * source used: https://snapshooter.com/learn/linux/find#basic-syntax

3. `-size`

First Example:
```
$ find ./technical -size 14k
./technical/biomed/1471-213X-2-8.txt
./technical/biomed/1471-2156-3-22.txt
./technical/biomed/1471-2180-2-29.txt
./technical/biomed/1471-230X-1-6.txt
./technical/biomed/1471-2350-4-4.txt
./technical/biomed/bcr635.txt
./technical/government/About_LSC/conference_highlights.txt
./technical/government/About_LSC/CONFIG_STANDARDS.txt
./technical/government/About_LSC/Protocol_Regarding_Access.txt
./technical/government/Env_Prot_Agen/tech_sectiong.txt
./technical/plos/journal.pbio.0020183.txt
./technical/plos/journal.pbio.0020311.txt
./technical/plos/journal.pbio.0020401.txt
./technical/plos/journal.pbio.0030024.txt
./technical/plos/journal.pbio.0030094.txt
./technical/plos/pmed.0020039.txt
./technical/plos/pmed.0020067.txt
```
This command finds all file sizes that are exactly 12kb in size. It could be useful if you wanted to find any file of a specific size.

Second Example:
```
$ find ./technical -size +200k
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-3.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/Env_Prot_Agen/bill.txt
./technical/government/Gen_Account_Office/d01591sp.txt
./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./technical/government/Gen_Account_Office/pe1019.txt
./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
```
This command finds all file sizes that are greater than 200kb in size with the `+` addition in the operator. Unlike the first command, this can be useful to find files over a specific size instead of files at that specific size, which can be useful for storage or troubleshooting. You can also find files under a certain size with a `-` operator.
   * source used: https://snapshooter.com/learn/linux/find#basic-syntax

5. `-exec`
   * source used:
https://linuxhandbook.com/find-exec-command/
