#### Python Full Course for Beginners [2025] - Mosh

Python 3.10.12 already installed on Ubuntu

```py
# Type python3 myfile.py on the command line

```

#### Python for Beginners - Learn Coding with Python in 1 Hour

```sh
sudo snap install pycharm-community --classic
```

`print, int, str, float, bool`

```python
name = input("What is your name")  
print("Hello" + name)  
first = input('enter a number: ')  
second = input('enter another number: ')  
  
third = float(first) + float(second)  
print('sum: ' + str(third))
```

**strings are IMMUTABLE**

The 'in' operator
```python
course = 'Python for Beginners'
print('Python' in course)
```
Result: *True*

#### Arithmetic Operators

```python
print(10 + 3)# 13
print(10 - 3)# 7  
print(10 * 3)# 30  
print(10 / 3)# 3.3333333333333335
print(10 // 3)# 3
print(10 % 3)# 1
print(10 ** 3)# 1000
x = 10  
x += 3 # Augmented assignment operator  
print(x)# 13  
```

#### Comparison Operators
`<,>, <=, >=, ==, != `

#### Logical Operators
`and, or, not `

#### If Statements
```python
temperature = 5  
if temperature > 30:  
    print("It's a hot day")  
    print("Drink plenty of water")  
elif temperature > 20:  
    print("It's a nice day")  
elif temperature > 10:  
    print("It's a bit cold")  
else:  
    print("It's cold")  
print("Done")
```

#### Exercise: write a function that weight in lbs to kg or the reverse
```python
weight = input("Weight?: ")  
unit = input("(K)g or (L)bs: ")  
  
if unit.lower() == 'l':  
    weight = round((float(weight) * .45359237),1)  
    print ("Weight in Kg: " + str(weight))  
else:  
    weight = round((float(weight)* 2.2),1)  
    print("Weight in lbs: " + str(weight))
```
Extra Credit: cause it to round to 1 decimal place
|                                      |
#### While loop
```python
i = 0  
limit = 10  
while i <= limit:  
    print(i * '*')  
    i += 1
```
output
![[Pasted image 20250509114722.png]]

#### Lists/Arrays
```python
names = ["John","Bob","Mosh","Sam","Mary"]  
print(names) ## output: ["John","Bob","Mosh","Sam","Mary"]  
print(names[1]) ## output: Bob  
print(names[-1]) ## output: Mary  
print(names[-2]) ## output: Sam  
print(names[0:3]) ## output:['John', 'Bob', 'Mosh']  
print(names) ## output: ["John","Bob","Mosh","Sam","Mary"]
```

#### List Functions
k