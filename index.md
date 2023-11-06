
Lab report 3.


Bug before code change: it reverses the order of items in the array until after the halfway point where it begins reversing everything back to the original order.
```
static void reverseInPlace(int[] arr) {
  for (int i = 0; i < arr.length; i += 1) {
    int temp = arr[i];
    arr[i]= arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```

Failure-inducing input in the buggy program:
```
@Test
public void testReverseInPlace() {
  int[] input1 = {1,2,3,4,5};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{5,4,3,2,1}, input1);
}
```


Input that does not induce a failure as a JUnit test:
```
@Test
  public void testReverseInPlace() {
  int[] input1 = {1}
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{1}, input1);
}
```

Symptom as the output of running the tests:

![image](https://github.com/Malakelis/cse15l-lab-reports/assets/63074465/9bdaf18a-81ad-449e-97d2-6eb557bf9e8e)

Code after bug fix: This fixes the code because instead of iterating through all of the elements and reversing the array twice and changing it back to the original array, it will now stop after about the halfway point where it has already reversed the array because if it goes further it will start reversing back to the original order.
```
static void reverseInPlace(int[] arr) {
  for (int i = 0; i < arr.length/2; i += 1) {
    int temp = arr[i];j
    arr[i]= arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```

Command chosen: Find - source used: https://www.redhat.com/sysadmin/linux-find-command
Four options: 
1. Can be used to list directories
2. Can find a single file by approximate name
3. Can find files by type
4. Can find empty files

Two examples for each option:
1. I use the find command in the home directory to navigate to the /docsearch/technical/ directory to print the two directories inside including the directory inside the folder and the two directories contained in the folder. 
command:
```
find ~/docsearch/technical/ -type d
```
output:
```
911report/ biomed/  
```

2. I use the find command in the home directory to navigate to the /home/docsearch/technical/biomed directory to print the single inside the folder as there is no other directory or folder in this directory.
command:
```
find ~/docsearch/technical/biomed/ -type d
```
output:
```
/home/docsearch/technical/biomed/
```

3. I use the find command in the /home/docsearch/technical directory to find all the files using a case insensitive search with the asteriks to find all files containing chapter-13 as their name.
command:
```
find / -iname "*chapter-13*txt"
```
output:
```
find: ‘/root’: Permission denied
find: ‘/opt/ed/bin’: Permission denied
/home/docsearch/technical/911report/chapter-13.4.txt
/home/docsearch/technical/911report/chapter-13.1.txt
/home/docsearch/technical/911report/chapter-13.3.txt
/home/docsearch/technical/911report/chapter-13.5.txt
/home/docsearch/technical/911report/chapter-13.2.txt
```

4.  I use the find command in the /home/docsearch/technical directory to find all the files using a case insensitive search with the asteriks to find all files containing preface as their name.
command:
```
find / -iname "*preface*"
```
output:
```
find: ‘/root’: Permission denied
find: ‘/opt/ed/bin’: Permission denied
/home/docsearch/technical/911report/preface.txt
/usr/lib/R/library/HSAUR/doc/preface.pdf
/usr/lib/R/library/HSAUR/doc/preface.R
/usr/lib/R/library/HSAUR/doc/preface.Rnw
```

5. I use the find command in the /home directory to filter and print out all the directories that are contained in the docsearch directory including the home directory.
command:
```
 find ~ -type d
```
output:
```
/home
/home/docsearch
/home/docsearch/lib
/home/docsearch/.git
/home/docsearch/.git/logs
/home/docsearch/.git/logs/refs
/home/docsearch/.git/logs/refs/remotes
/home/docsearch/.git/logs/refs/remotes/origin
/home/docsearch/.git/logs/refs/heads
/home/docsearch/.git/info
/home/docsearch/.git/objects
/home/docsearch/.git/objects/info
/home/docsearch/.git/objects/pack
/home/docsearch/.git/refs
/home/docsearch/.git/refs/tags
/home/docsearch/.git/refs/remotes
/home/docsearch/.git/refs/remotes/origin
/home/docsearch/.git/refs/heads
/home/docsearch/.git/hooks
/home/docsearch/.git/branches
/home/docsearch/technical
/home/docsearch/technical/911report
/home/docsearch/technical/biomed
```

6. I use the find command in the /home/docsearch/ directory to filter and print out all the directories in that directory which is only one in this case as there is only one directory in the lib folder.
command:
```
find ~/docsearch/lib/ -type d
```
output:
```
/home/docsearch/lib/
```

7. I use the find command here in the home directory to print out all the files that are empty where many of them seem to be in the /home/docsearch/technical/biomed/ directory
command:
```
find ~ -type f -empty
```
output:
```
/home/docsearch/technical/biomed/ar149.txt
/home/docsearch/technical/biomed/1476-9433-1-3.txt
/home/docsearch/technical/biomed/1476-511X-1-2.txt
/home/docsearch/technical/biomed/1476-511X-2-3.txt
/home/docsearch/technical/biomed/1476-0711-2-3.txt
/home/docsearch/technical/biomed/ar331.txt
/home/docsearch/technical/biomed/1477-7827-1-43.txt
/home/docsearch/technical/biomed/1477-5956-1-1.txt
/home/docsearch/technical/biomed/ar612.txt
/home/docsearch/technical/biomed/bcr45.txt
/home/docsearch/technical/biomed/ar624.txt
/home/docsearch/technical/biomed/bcr635.txt
/home/docsearch/technical/biomed/bcr588.txt
/home/docsearch/technical/biomed/1477-7827-1-21.txt
/home/docsearch/technical/biomed/bcr284.txt
/home/docsearch/technical/biomed/1476-4598-2-3.txt
/home/docsearch/technical/biomed/1478-1336-1-2.txt
/home/docsearch/technical/biomed/ar130.txt
/home/docsearch/technical/biomed/ar68.txt
/home/docsearch/technical/biomed/bcr273.txt
/home/docsearch/technical/biomed/1475-9268-1-1.txt
/home/docsearch/technical/biomed/1476-069X-2-7.txt
/home/docsearch/technical/biomed/bcr583.txt
/home/docsearch/technical/biomed/1475-925X-2-1.txt
/home/docsearch/technical/biomed/1477-7827-1-9.txt
/home/docsearch/technical/biomed/bcr567.txt
/home/docsearch/technical/biomed/1476-5918-1-2.txt
/home/docsearch/technical/biomed/1475-9276-1-3.txt
/home/docsearch/technical/biomed/ar429.txt
/home/docsearch/technical/biomed/1475-925X-2-10.txt
/home/docsearch/technical/biomed/bcr317.txt
/home/docsearch/technical/biomed/1477-7525-1-9.txt
/home/docsearch/technical/biomed/1475-9268-1-2.txt
/home/docsearch/technical/biomed/ar619.txt
/home/docsearch/technical/biomed/ar799.txt
/home/docsearch/technical/biomed/1477-7525-1-10.txt
/home/docsearch/technical/biomed/1476-4598-2-2.txt
/home/docsearch/technical/biomed/1476-4598-1-6.txt
/home/docsearch/technical/biomed/ar104.txt
/home/docsearch/technical/biomed/1477-7827-1-46.txt
/home/docsearch/technical/biomed/1476-4598-2-22.txt
/home/docsearch/technical/biomed/ar328.txt
/home/docsearch/technical/biomed/bcr285.txt
/home/docsearch/technical/biomed/1478-1336-1-4.txt
/home/docsearch/technical/biomed/ar745.txt
/home/docsearch/technical/biomed/1477-7827-1-54.txt
/home/docsearch/technical/biomed/1476-4598-1-3.txt
/home/docsearch/technical/biomed/ar309.txt
/home/docsearch/technical/biomed/ar79.txt
/home/docsearch/technical/biomed/ar383.txt
/home/docsearch/technical/biomed/1475-925X-2-6.txt
/home/docsearch/technical/biomed/bcr618.txt
/home/docsearch/technical/biomed/1477-7525-1-12.txt
/home/docsearch/technical/biomed/1476-511X-2-2.txt
/home/docsearch/technical/biomed/1475-925X-2-12.txt
/home/docsearch/technical/biomed/1476-072X-2-4.txt
/home/docsearch/technical/biomed/ar774.txt
/home/docsearch/technical/biomed/bcr605.txt
/home/docsearch/technical/biomed/1476-069X-2-4.txt
/home/docsearch/technical/biomed/1477-7827-1-17.txt
/home/docsearch/technical/biomed/1478-1336-1-3.txt
/home/docsearch/technical/biomed/bcr607.txt
/home/docsearch/technical/biomed/1476-4598-2-1.txt
/home/docsearch/technical/biomed/ar297.txt
/home/docsearch/technical/biomed/1476-072X-2-3.txt
/home/docsearch/technical/biomed/bcr620.txt
/home/docsearch/technical/biomed/1476-9433-1-2.txt
/home/docsearch/technical/biomed/ar422.txt
/home/docsearch/technical/biomed/1477-7819-1-10.txt
/home/docsearch/technical/biomed/1476-4598-1-8.txt
/home/docsearch/technical/biomed/ar321.txt
/home/docsearch/technical/biomed/1476-4598-1-5.txt
/home/docsearch/technical/biomed/ar792.txt
/home/docsearch/technical/biomed/1476-4598-2-28.txt
/home/docsearch/technical/biomed/1476-069X-2-9.txt
/home/docsearch/technical/biomed/1477-7827-1-6.txt
/home/docsearch/technical/biomed/1476-4598-2-24.txt
/home/docsearch/technical/biomed/bcr294.txt
/home/docsearch/technical/biomed/bcr458.txt
/home/docsearch/technical/biomed/ar387.txt
/home/docsearch/technical/biomed/ar118.txt
/home/docsearch/technical/biomed/1475-925X-2-11.txt
/home/docsearch/technical/biomed/bcr602.txt
/home/docsearch/technical/biomed/ar778.txt
/home/docsearch/technical/biomed/1477-7827-1-13.txt
/home/docsearch/technical/biomed/1478-7954-1-3.txt
/home/docsearch/technical/biomed/ar120.txt
/home/docsearch/technical/biomed/1477-7827-1-23.txt
/home/docsearch/technical/biomed/1477-7827-1-27.txt
/home/docsearch/technical/biomed/bcr570.txt
/home/docsearch/technical/biomed/bcr571.txt
/home/docsearch/technical/biomed/1477-7827-1-48.txt
/home/docsearch/technical/biomed/ar795.txt
/home/docsearch/technical/biomed/ar409.txt
/home/docsearch/technical/biomed/1476-4598-2-25.txt
/home/docsearch/technical/biomed/bcr568.txt
/home/docsearch/technical/biomed/ar430.txt
/home/docsearch/technical/biomed/ar408.txt
/home/docsearch/technical/biomed/ar140.txt
/home/docsearch/technical/biomed/ar407.txt
/home/docsearch/technical/biomed/ar750.txt
/home/docsearch/technical/biomed/ar601.txt
/home/docsearch/technical/biomed/1476-4598-2-20.txt
/home/docsearch/technical/biomed/ar93.txt
/home/docsearch/technical/biomed/bcr303.txt
/home/docsearch/technical/biomed/ar319.txt
/home/docsearch/technical/biomed/1477-7827-1-36.txt
/home/docsearch/technical/biomed/1476-069X-1-3.txt
/home/docsearch/technical/biomed/1476-0711-2-7.txt
/home/docsearch/technical/biomed/bcr631.txt
/home/docsearch/technical/biomed/ar615.txt
/home/docsearch/technical/biomed/1476-069X-2-2.txt
/home/docsearch/technical/biomed/1477-7827-1-31.txt
/home/docsearch/technical/biomed/1475-925X-2-3.txt
```

8. I use the find command here in the /home/docsearch/technical directory to print out all the files that are empty in this directory.
command:
```
find ~ -type f -empty
```
output:
```
/home/docsearch/technical/biomed/ar149.txt
/home/docsearch/technical/biomed/1476-9433-1-3.txt
/home/docsearch/technical/biomed/1476-511X-1-2.txt
/home/docsearch/technical/biomed/1476-511X-2-3.txt
/home/docsearch/technical/biomed/1476-0711-2-3.txt
/home/docsearch/technical/biomed/ar331.txt
/home/docsearch/technical/biomed/1477-7827-1-43.txt
/home/docsearch/technical/biomed/1477-5956-1-1.txt
/home/docsearch/technical/biomed/ar612.txt
/home/docsearch/technical/biomed/bcr45.txt
/home/docsearch/technical/biomed/ar624.txt
/home/docsearch/technical/biomed/bcr635.txt
/home/docsearch/technical/biomed/bcr588.txt
/home/docsearch/technical/biomed/1477-7827-1-21.txt
/home/docsearch/technical/biomed/bcr284.txt
/home/docsearch/technical/biomed/1476-4598-2-3.txt
/home/docsearch/technical/biomed/1478-1336-1-2.txt
/home/docsearch/technical/biomed/ar130.txt
/home/docsearch/technical/biomed/ar68.txt
/home/docsearch/technical/biomed/bcr273.txt
/home/docsearch/technical/biomed/1475-9268-1-1.txt
/home/docsearch/technical/biomed/1476-069X-2-7.txt
/home/docsearch/technical/biomed/bcr583.txt
/home/docsearch/technical/biomed/1475-925X-2-1.txt
/home/docsearch/technical/biomed/1477-7827-1-9.txt
/home/docsearch/technical/biomed/bcr567.txt
/home/docsearch/technical/biomed/1476-5918-1-2.txt
/home/docsearch/technical/biomed/1475-9276-1-3.txt
/home/docsearch/technical/biomed/ar429.txt
/home/docsearch/technical/biomed/1475-925X-2-10.txt
/home/docsearch/technical/biomed/bcr317.txt
/home/docsearch/technical/biomed/1477-7525-1-9.txt
/home/docsearch/technical/biomed/1475-9268-1-2.txt
/home/docsearch/technical/biomed/ar619.txt
/home/docsearch/technical/biomed/ar799.txt
/home/docsearch/technical/biomed/1477-7525-1-10.txt
/home/docsearch/technical/biomed/1476-4598-2-2.txt
/home/docsearch/technical/biomed/1476-4598-1-6.txt
/home/docsearch/technical/biomed/ar104.txt
/home/docsearch/technical/biomed/1477-7827-1-46.txt
/home/docsearch/technical/biomed/1476-4598-2-22.txt
/home/docsearch/technical/biomed/ar328.txt
/home/docsearch/technical/biomed/bcr285.txt
/home/docsearch/technical/biomed/1478-1336-1-4.txt
/home/docsearch/technical/biomed/ar745.txt
/home/docsearch/technical/biomed/1477-7827-1-54.txt
/home/docsearch/technical/biomed/1476-4598-1-3.txt
/home/docsearch/technical/biomed/ar309.txt
/home/docsearch/technical/biomed/ar79.txt
/home/docsearch/technical/biomed/ar383.txt
/home/docsearch/technical/biomed/1475-925X-2-6.txt
/home/docsearch/technical/biomed/bcr618.txt
/home/docsearch/technical/biomed/1477-7525-1-12.txt
/home/docsearch/technical/biomed/1476-511X-2-2.txt
/home/docsearch/technical/biomed/1475-925X-2-12.txt
/home/docsearch/technical/biomed/1476-072X-2-4.txt
/home/docsearch/technical/biomed/ar774.txt
/home/docsearch/technical/biomed/bcr605.txt
/home/docsearch/technical/biomed/1476-069X-2-4.txt
/home/docsearch/technical/biomed/1477-7827-1-17.txt
/home/docsearch/technical/biomed/1478-1336-1-3.txt
/home/docsearch/technical/biomed/bcr607.txt
/home/docsearch/technical/biomed/1476-4598-2-1.txt
/home/docsearch/technical/biomed/ar297.txt
/home/docsearch/technical/biomed/1476-072X-2-3.txt
/home/docsearch/technical/biomed/bcr620.txt
/home/docsearch/technical/biomed/1476-9433-1-2.txt
/home/docsearch/technical/biomed/ar422.txt
/home/docsearch/technical/biomed/1477-7819-1-10.txt
/home/docsearch/technical/biomed/1476-4598-1-8.txt
/home/docsearch/technical/biomed/ar321.txt
/home/docsearch/technical/biomed/1476-4598-1-5.txt
/home/docsearch/technical/biomed/ar792.txt
/home/docsearch/technical/biomed/1476-4598-2-28.txt
/home/docsearch/technical/biomed/1476-069X-2-9.txt
/home/docsearch/technical/biomed/1477-7827-1-6.txt
/home/docsearch/technical/biomed/1476-4598-2-24.txt
/home/docsearch/technical/biomed/bcr294.txt
/home/docsearch/technical/biomed/bcr458.txt
/home/docsearch/technical/biomed/ar387.txt
/home/docsearch/technical/biomed/ar118.txt
/home/docsearch/technical/biomed/1475-925X-2-11.txt
/home/docsearch/technical/biomed/bcr602.txt
/home/docsearch/technical/biomed/ar778.txt
/home/docsearch/technical/biomed/1477-7827-1-13.txt
/home/docsearch/technical/biomed/1478-7954-1-3.txt
/home/docsearch/technical/biomed/ar120.txt
/home/docsearch/technical/biomed/1477-7827-1-23.txt
/home/docsearch/technical/biomed/1477-7827-1-27.txt
/home/docsearch/technical/biomed/bcr570.txt
/home/docsearch/technical/biomed/bcr571.txt
/home/docsearch/technical/biomed/1477-7827-1-48.txt
/home/docsearch/technical/biomed/ar795.txt
/home/docsearch/technical/biomed/ar409.txt
/home/docsearch/technical/biomed/1476-4598-2-25.txt
/home/docsearch/technical/biomed/bcr568.txt
/home/docsearch/technical/biomed/ar430.txt
/home/docsearch/technical/biomed/ar408.txt
/home/docsearch/technical/biomed/ar140.txt
/home/docsearch/technical/biomed/ar407.txt
/home/docsearch/technical/biomed/ar750.txt
/home/docsearch/technical/biomed/ar601.txt
/home/docsearch/technical/biomed/1476-4598-2-20.txt
/home/docsearch/technical/biomed/ar93.txt
/home/docsearch/technical/biomed/bcr303.txt
/home/docsearch/technical/biomed/ar319.txt
/home/docsearch/technical/biomed/1477-7827-1-36.txt
/home/docsearch/technical/biomed/1476-069X-1-3.txt
/home/docsearch/technical/biomed/1476-0711-2-7.txt
/home/docsearch/technical/biomed/bcr631.txt
/home/docsearch/technical/biomed/ar615.txt
/home/docsearch/technical/biomed/1476-069X-2-2.txt
/home/docsearch/technical/biomed/1477-7827-1-31.txt
/home/docsearch/technical/biomed/1475-925X-2-3.txt
```
   
