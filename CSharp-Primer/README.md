# C# Primer

C# for Unity is not as complex as C# in a .NET application. It is simplified. Some things to remember about C#:

*	**It's COOL!** - No, really, originally Microsoft called it COOL for C-like Object Oriented Language.

*	**It is Case Sensitive** - AFunction and AFuNcTiOn would be two different things in the eyes of C#

*	**Uses Dot Syntax** - To access methods or variables of a class you use a period. If the class Person has a variable called "age" you can access it like Person.age

## Basic Class
In Unity, when you create a script, it creates a Class. This class is an extension of MonoBehaviour. In C#, you can inherit features of other classes this way.

```cs
using UnityEngine;
using System.Collection; 
public class Script : MonoBehaviour
{

}
```

## Comments

In C#, you can make a comment which is not processed in 2 ways

Single line comments - start with two slashes

```cs
 // Single Line of Comments!
```

Or if you want to comment a block of text you can start with a /* and end with a */. Everything in-between will be considered a comment:

```
/*
 * This is a multiline comments
 */
 ```
Commenting your code is important for helping you remember what your code is doing as well as helping other understand your code and why you chose to do things a certain way. 

## Variables

To declare a variable in C# you have to declare it's type and then it's name. Unity uses 5 basic datatypes of C#:

*	**Boolean type**  - True or False

	```cs
    bool aBoolean = false;   // can only be "true" or "false";
    // NOTE a bool in C# cannot be used as a 1 or 0 like in other languages!
	```
	
*	**Integral types** -  whole numbers
	
	```cs
	int anInteger = 318433;             // 32bits   -2,147,483,648 to 2,147,483,647
	```
	
*	**Characters** - as UNICODE values
	
	```cs
	char aCharacter;                    // 16bits   0 to 65,535
	```
	
*	**String** - UNICODE Text
	
	```cs
	string aString = "A bunch of text" 
	```
	
*	**Decimals**
	
	```cs
	float aFloatingPoint;               // 32bits   7 digit precision       1.5 x 10^-45 to 3.4 x 10^38
	double aDoublePrecision;            // 64bits   15-16 digits            5.0 x 10^-324 to 1.7 x 10^308
	```

## Accessibility

When you start to declare methods and member variables, you have to instruct the compiler what can have access to it.

By default, all variables, methods and classes are "private". If you want them to be accessed by other Classes or the Unity Editor, you need to make the "public".
There are 3 types that you will be using

*	**Public** - Anyone can modify it
	
*	**Private** - Only this class can modify it
	
*	**Protected** - Only this class and derived classes can modify it.

## Member Variables

In you class, you can define member variables which will be available throughout the class.

```cs
using UnityEngine;
using System.Collection; 
public class Script : MonoBehaviour
{
    int aMethodVariable = 0;
    public int aPublicMethodVariable = 0;
}
```

## Methods

Methods are reusable chunks of code.  The are defined by 

```cs
<accessibility> <return datatype> <method name> ( <parameters>) {
    <method body>
}
```

* **Accessibility** - What can access this method. If you  do not put anything here, it is assumed to be "private".
* **Return Datatype** - What kind of information is returned from this method. If it does not return anything, you need to say "void".
* **Method Name** - The name of the method. Each method needs a unique name.
* **Parameters** - These are options, this would be a list of variables that you can send to the method. They are a comma seperated list, where they are defined as <datatype> <variable names> 
* **Method Body** - This is where all the code happens for the method.

```cs
using UnityEngine;

using System.Collection; 
public class Script : MonoBehaviour
{
    protected void aMethodWithParameters(int aNumber, float anotherNumber) {
    	// Code goes here...
    } 
}
```

## Statics

This means, no matter how many instances of this class, there will only be one of these which will be shared through every instance.  You can make a method or variable static. However, if you make a method static, it can only use method variables that are static!

## Math Operations

*	**\+**	Addition
*	**\-**	Subtraction
*	__*__	Multiplication
*	**/**   Division
*	**%**	Modulus (remainder)
*	**+=**	Add to self (instead of writing something like a = a + 2;, you could do a += 2;)
*	**-=**	Subtract from self
*	__*=__	Multiply self
*	**/=**	Divide self
*	**++**	Increment (add one to self)
*	**--**	Decrement (subtract one from self)

## Relational Operations

*	**==** - Is equal
*	**!=** - Is not equal
*	**>** - Is greater than
*	**<** - Is less than
*	**>=** - Is greater or equal to
*	**<=** - Is less than or equal to

## Logical Operations

*	**&&**	- Logical And
*	**||**	- Logical Or
*	**!**	- Logical Not

## Conditional Statements

The condition can be a simple boolean to check or can be relation operation between two variables. If you want to check between several variables, you will need to compare two variables and use a Logical Operation to tie together the checks. The "if" statement is the most common.

```cs
if(condition) {
    // This happens only if the condition is true
}
```

You can also do something incase that condition is not true:

```cs
if(condition) {
   // This happens only if the condition is true
} else {
   // This happens only if the condition is false
}
```

You can also check different conditions in a condition is not met.

```cs
if(condition) {
   // This happens only if this condition is true
} else if(another condition) {
   // This happens only if the "another condition" is true
} else {
   // This happens only if neither of the condition is true
}
```

## Loops

### While Loop   
```cs
while (condition)
{
	// Do something here...
}
```

### Do Loop
```cs
do
{
    aShortByte--;
    Console.WriteLine("Do = {0} ", aShortByte);
} while (aShortByte >= 0);
```

The main difference between the While and Do While is that Do While will happen at least once since the condition is checked at the end of the loop.

### For Loop

Has three parts to it:

```cs
for ( <initializer>, <condition>, <incrementation> ) 
```

* **Initializer** - The variable that the loop will check. 
* **Condition** - When the loop should be executed.
* **Incrementation** - When the code block for the loop has ended, the initializer will be modified by this

	```cs
    for (int counter = 0; counter < 10; counter++)
    {
        print("Counter =  " + counter);
    }
	```
	            
	This will print out the following:
	
	```cs
	Counter = 0 
	Counter = 1
	Counter = 2
	Counter = 3
	Counter = 4
	Counter = 5
	Counter = 6
	Counter = 7
	Counter = 8
	Counter = 9
	```
