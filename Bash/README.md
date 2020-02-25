# Bash

## Basic

- `#!/bin/bash` indicates which interpreter use
- **#** after that is a comment
- **echo** printe what follow
  - echo "Hello World" or use a variable echo "hello **\$variableName**"
- _define a variable_
  - **variableName=variableValue**, name="name value" or i=4 (NOTE without space between _=_)
- execute action with variable **\$((action to do))** es. _y=\$((i+x))_
- **cat<<End some texts End** print the text

## Functions

```bash
# is a global variable
name="Paul"
getDate(){
    # is a local variable
    local name="Jerry"
    date
    return
}
#call function
getDate
```

## Get and return Parameter Function Value

```bash
getSum(){
    local num1=$1
    local num2=$2
    local sum=$((num1+num2))
    echo $sum
}
num1=3
num2=10
sum=$(getSum num1 num2)
echo "The sum is $sum"
```

## Read from User

```bash
read -p "What is your name?" name
echo "Hello $name"

```

- _-p_ common input
- _-sp_ secret input

## Conditional

```bash
age=17
if [$age -ge 16] #greater or equal
then
    echo "You can drive"
elif [$age -eq 15] ## equal
then
    echo "You can drive next year"
else
    echo "Here we go"
if
# another way

if ((age >= 10)); then
    echo "Your number is equal to ten"
else
    echo "Something"
fi

if (( ((age % 2)) == 0)); then
    echo "Something"
fi

if (( ((age>=18)) && ((age<=60)))); then
    echo "Something"
fi
```

- **-ge** greater or equal
- **-le** less or equal
- **-ep** equal
- **-ne** not equal
- **-gt** greater than
- **-lt** less than

## Regular Expression

```bash
pat="^[0-9]{8}$"
if [[$input = ~$pat]]; then
    echo "..."
```

## Parameter Expansion

`${variableName expantion command}`

## Loop

```bash
num=0
while [$num -le 10]; do
    echo $num
    num=$((num+1))
done

for ((i=0; i<=10; i=i+1));do
    echo $i
done
for i in {A..Z}; do
    echo $i
done
## exist continue command and break ^_^

```

## Array

```bash
fav_nums=(1 2 3.5 24 5)
echo "${fav_nums[0]}"
fav_nums[0]=1
fav_nums+=(1 7) # add 1 and 7 to our array

for i in ${fav_nums[*]}; do
    echo $i  # print value
done
for i in ${fav_nums[@]}; do
    echo $i  # print index
done
```
