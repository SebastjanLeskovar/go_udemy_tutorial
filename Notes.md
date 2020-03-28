# Notes

## Go CLI

**go build**

Compiles a bunch of go source code files.

After it is compiled, run the program with ./main (Unix) or main.exe (Windows).

**go run**

Compiles and executes one or two files.

**go fmt**

Formats all the code in each file in the current directory. 

**go install**

Compies and "installs" a package.

**go get**

Downloads the raw source code of someone else's package. 

**go test**

Runs any tests associated with the current project. 

## What is a package

Package in Go means the same as project or workspace. 

A package can contain multiple files. Each file must start with the line that states what package does the file belong to. 

Types of packages:
 - Executable

Generates a file that we can run.

 - Reusable

Code used as "helpers". Good place to put reusable logic.

(start with 3_cards)

# Notes

## Types of languages

Dynamic types

Javascript, Ruby, Python

We do not care what values we are assigning to any given variable. 

Static types

C++, Java, Go

When we define a variable, we assign it a type.

## basic Go types

Type        Example
-----------------------------------------
bool        true, false
string      "Hi!", "How is it going?"
int         0, -10000, 99999
float64     10.000001, 0.00009, -100.003

## Functions

Define a function: 

```
func newCard() string {
    return "Five of Diamonds"
}
```

Functions must define return type. 

## Arrays and slices

Arrays have fixed length while slices do not. They can contain only one type of elements.

Declare a slice:

```
cards := []string {"Ace of Diamonds", newCard()}
```

Add a new string:

cards = append(cards, "Six of Spades")

## Iteration

```
for i, card := range cards {
    fmt.Println(i, card)
}
```

## Receiver function

```
func (d deck) print() {

}
```

d = the vorking variable / the actual copy of the deck we are working with is available as a variable called 'd'. In Python, the equivalent of 'd' is self. 

This receiver function is of type 'deck' and the function name is deck. Receiver sets up methods on variables that we create.

Any variable of type 'deck' now gets access to the 'print' method. 

## Slice range syntax

fruits = ["apple", "banana", "grape", "orange"]

fruits[StartIndexIncluding: upToNotIncluding]

fruits[0:2] = ["apple", "banana"]

## Multiple return values

func deal(d deck, handSize int) (deck, deck) {
	return d[:handSize], d[handSize:]
}

## Byte slices

Library ioutil enables us to write files to drive and load them.

`func WriteFile(filename string, data []byte, perm os.FileMode) error`

Function WriteFile is used to create or write to a new or existing file on local hard drive.

### Byte slice

"Hi there!" => string

[72 105 32 116 104 101 114 101 33] => byte slice

## Type conversion

[]byte("Hi there!")

Here, we turn the string "Hi there!" into a bite slice. 

## Tests

Tests are written in files named <filename>_test.go. 

(start with 4_structs)

# Structs

## Declaring structs

```
type person struct {
	firstName string
	lastName  string
}
```

## Create a struct instance

alex := person{"Alex", "Anderson"}

alex := person{firstName: "Alex", lastName: "Anderson"}

var alex person

If we declare the variable like this, Go automatically fills the fields we did not specify with zero values.

string -> ""
int -> 0
float -> 0
bool -> false

## Embed a struct inside another struct

type contactInfo struct {
	email   string
	zipCode int
}

type person struct {
	firstName string
	lastName  string
	contact   contactInfo
}

## Pointers

Go is a pass by value language. That means that whenever we pass some value into a function, Go will take that data and place it inside a new container in RAM.

If eg. we do `jim.updateName("Jimmy")`, this will not change the name of object jim, but will create a new object and give it name "Jimmy".

### Ampersand

`&variable`: Give me the memory address of the value this variable is pointing at

If we say `jimPointer := &jim`, jimPointer does not directly point to the struct. It is a reference to the memory address where the struct exists at.

`*pointer`: Give me the value this memory address is pointing at.

For example, `*jimPointer` returns the actual struct of type person. 

Asterix can mean two things:

func (pointerToPerson *person) updateName() {
	*pointerToPerson
}

For *person, it is a type description - it means we're working with a pointer to a person.

For *pointerToPerson, it is an operator - it means we want to manipulate the value the pointer is referencing.

Address: 0001 (jimPointer)
Value: person{firstName: "Jim"...} (jim)

Turn address into value with *address (*pointerToPerson)
Turn value into address with &value (&jim)
