Bash_scripting Cheatsheet==================https://devhints.io/bash
https://dheeraj3choudhary.com/linux-for-devops-or-shell-script-for-operators-decision-making-statements
https://github.com/jidibinlin/Free-DevOps-Books-1/blob/master/book/Linux%20Shell%20Scripting%20Essentials.pdf

# Shell_scripting
============================================
echo "enter your name"
read NAME 
echo "Your name is ${NAME}"

**Output:**
enter your name
vijay
Your name is vijay
============================================
WD=$(pwd)
echo "current working dir is ${WD}"

**Output:**
current working dir is cloudops/usr
============================================
WD=$(pwd)
echo "enter the name of new directory"
read new_dir_name
NEW_DIR_PATH="${WD}/${new_dir_name}"
mkdir $NEW_DIR_NAME
echo "New dir is created at $NEW_DIR_NAME"

**Output:**
enter the name of new directory
vijay
New dir is created at cloudops/vijay
============================================
TO CHECK THE LENGTH OF STRING OR THE CONTENTET ASSIGNED UNDER VARIABLE
NEW_VARIABLE="this is just a script"
echo ${#NEW_VARIABLE}

**Output:**
22
============================================
USE OF FOR LOOP 
for i in {1..20};do
echo "current index is ${i}"
done

**Output:**
current index is 1
current index is 2
current index is 3
.
.
current index is 20
============================================
echo "enter the file you want to read"
read file_name
cat $file_name | while 
read line; do
echo $line 
done 

**Output:**
enter the file you want to read
vijay.txt
<content of vijay file>
============================================
USE OF FUNCTION 
myfunc(){
echo "Good morning .. $1"
}
myfunc $1

**Output:**
#./<file_name> vijay
Good morning .. vijay
============================================
PASSING MULTIPLR VALUES 
myfunc(){
echo "Good morning .. $1 and $2"
}
myfunc $1 $2

**Output:**
#./<file_name> vijay kapil
Good morning .. vijay and kapil
============================================
GET FUNCTION USING LOCAL VARIABLE 
getfunction(){
local expectedResult= "some input"
read $expectedResult
}
result="$(getfunction)"
echo "Resuilt is : ${result}"

**Output:**
Resuilt is : some input
============================================
WE CANNOT PASS INPUT PARAMETER INSIDE FUNCTION , WE NEED TO USE IT OUTSIDE OF FUNCTION
getfunction(){
local expectedResult= "some input"
read $expectedResult
}
echo "enter your input"
read userInput
result="$(getfunction $userInput)"
echo "Resuilt is : ${result}"

**Output:**
enter your input
test
Resuilt is : test
============================================
echo "Enter the name of person"
read NAME
if [[ NAME != "vijay" ]]; then 
echo "You are not vijay"
fi

**Output:**
Enter the name of person
vijay
You are not vijay
============================================
echo "Enter the name of person"
read NAME
if [[ $NAME != "vijay" ]]; then 
echo "You are not vijay"
else
echo "you are ${NAME}"
fi

**Output:**
Enter the name of person
vijay
you are vijay

Enter the name of person
kapil
you are not vijay
============================================
SAMPLE_VARIABLE=$1
if [[ -z $SAMPLE_VARIABLE ]]; then
echo "Pass some value in the paramter"
elif [[ $SAMPLE_VARIABLE == "na" ]]; then 
echo "Pass some meaningful value"
else
echo "Thank you"
fi

**Output:**
#./<file_name> na
Pass some meaningful value
#./<file_name> hi
Thank you
============================================
for HOST in host1 host2 host3; do 
echo $HOST
done 

**Output:**
host1
host2
host3
============================================
#! /bin/bash
for HOST in host{1..20}; do
echo $HOST
done

**Output:**
host 1
host 2
.
.
host 20
============================================
#!/bin/bash
for file in 'ls /Downloads' ; do
echo $file
done

**Output:**
It will list the files in downloads folder 
============================================
**Use of $0, $1, $@, $* and $#**

#! /bin/bash
echo "file name: $0"
echo "first parameter: $1"
echo "second parameter: $2"
echo "total values: $@"
echo "total values: $*"
echo "Total numbers of parameters: $#"

execute file by giving input as below 
### ./ega.sh vijay gawate
**Output:**
file name: ./ega.sh
first parameter: vijay
second parameter: gawate
total values: vijay gawate
total values: vijay gawate
Total numbers of parameters: 2
============================================
**For loop using $* **

#! /bin/bash
for TOKEN in $*
do
echo $TOKEN
done

**Output:**
it will print all the content we supply while executing script 
./ega.sh vijay is smart 

Actual output:----
vijay
is smart 
============================================
**Use of $?**
 
#echo $?
it will give status of privious commands or scripts upon its completion
if exit status is 0 : then the cmd or script is successful 
if exit status is 1 : then the cmd or script is unsuccessful 
============================================
**Use of array in scripting**
 
#! /bin/bash 
NAME[0]="Vijay"
NAME[1]="Kapil"
NAME[2]="Vishal"
NAME[3]="Suyog"
NAME[4]="Vaibhav"
echo "First index is : ${NAME[0]}"
echo "Second indes is : ${NAME[1]}"

**Output:**
First index is : Vijay
Second indes is : Kapil
============================================
#! /bin/bash 
NAME[0]="Vijay"
NAME[1]="Kapil"
NAME[2]="Vishal"
NAME[3]="Suyog"
NAME[4]="Vaibhav"
echo "First index is : ${NAME[*]}"
echo "Second indes is : ${NAME[@]}"

**Output:**
First index is : Vijay Kapil Vishal Suyog Vaibhav
Second indes is : Vijay Kapil Vishal Suyog Vaibhav
============================================
**Mathematical operators in Shell scripting **
#/bin/bash 
val=`expr 2 + 2`
echo "Total is : $val"

**Output:**
Total is : 4
============================================
#/bin/bash
a=10
b=30
val=`expr $a + $b`
echo "Total is : $val"

**Output:**
Total is : 40
============================================
#/bin/bash 
a=10
b=30
if [ $a != $b ] 
then
  echo "a is not  equal to b"
fi

**Output:**
a is not equal to b
============================================
#/bin/bash
a=10
b=30
if [ $a -lt $b ]
then
  echo "a is not less than  b"
fi

**Output:**
a is not less than  b
============================================
#!/bin/sh

a=10
b=20

if [ $a -eq $b ]
then
   echo "$a -eq $b : a is equal to b"
else
   echo "$a -eq $b: a is not equal to b"
fi

if [ $a -ne $b ]
then
   echo "$a -ne $b: a is not equal to b"
else
   echo "$a -ne $b : a is equal to b"
fi

if [ $a -gt $b ]
then
   echo "$a -gt $b: a is greater than b"
else
   echo "$a -gt $b: a is not greater than b"
fi

if [ $a -lt $b ]
then
   echo "$a -lt $b: a is less than b"
else
   echo "$a -lt $b: a is not less than b"
fi

if [ $a -ge $b ]
then
   echo "$a -ge $b: a is greater or  equal to b"
else
   echo "$a -ge $b: a is not greater or equal to b"
fi

if [ $a -le $b ]
then
   echo "$a -le $b: a is less or  equal to b"
else
   echo "$a -le $b: a is not less or equal to b"
fi

**Output:**
10 -eq 20: a is not equal to b
10 -ne 20: a is not equal to b
10 -gt 20: a is not greater than b
10 -lt 20: a is less than b
10 -ge 20: a is not greater or equal to b
10 -le 20: a is less or  equal to b
============================================
**Boolen operators:**
#!/bin/sh

a=10
b=20

if [ $a != $b ]
then
   echo "$a != $b : a is not equal to b"
else
   echo "$a != $b: a is equal to b"
fi

if [ $a -lt 100 -a $b -gt 15 ]
then
   echo "$a -lt 100 -a $b -gt 15 : returns true"
else
   echo "$a -lt 100 -a $b -gt 15 : returns false"
fi

if [ $a -lt 100 -o $b -gt 100 ]
then
   echo "$a -lt 100 -o $b -gt 100 : returns true"
else
   echo "$a -lt 100 -o $b -gt 100 : returns false"
fi

if [ $a -lt 5 -o $b -gt 100 ]
then
   echo "$a -lt 100 -o $b -gt 100 : returns true"
else
   echo "$a -lt 100 -o $b -gt 100 : returns false"
fi

**Output:**
10 != 20 : a is not equal to b
10 -lt 100 -a 20 -gt 15 : returns true
10 -lt 100 -o 20 -gt 100 : returns true
10 -lt 5 -o 20 -gt 100 : returns false
============================================
