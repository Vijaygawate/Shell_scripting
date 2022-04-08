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
