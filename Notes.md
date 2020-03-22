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