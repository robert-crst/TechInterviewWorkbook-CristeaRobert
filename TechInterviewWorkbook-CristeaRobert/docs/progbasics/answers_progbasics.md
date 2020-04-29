# Programming Basics questions

```python
print("Hello world")
```

## Computer science

#### Data structures

-   What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
```
      In general, lists(array):
        - are most flexible ordered collection object type; can contain any sort of object
        - are mutable object (may be changed)
        - is useful because it removes the cognitive load of having to remember things

      List = list(object) // [] // [object] // [[][]] ...

      Some methods that i usually use:
        - len(List)                  lenght of list (index start from 0)
        - List.index(element)        index of a specified element
        - List.append(element)       add one element at the end of list
        - del List[element]          i prefer it instead of List.remove(element)
        - and many more...
```

-   What is the difference between a list/array and a set?
```
      I said above what lists are. Now, a set is an unordered collection data type that is not iterable(elements
      dont have a specified order, they can change place any time), and has no duplicate elements.
      Now a major difference is that sets are slightly faster when it comes to check if one element it s
      present, and list are faster and more usefull when you want to iterate.
```

-   What is the purpose and methods of a dictionary/map data structure?
```
      Python dictionaries are something completely different - they are not sequences at all, but are instead known as mappings.
      Mappings are also collections of other objects, but they store objects by key instead of by relative position.
      In fact, mappings don’t maintain any reliable left-to-right order; they simply map keys to associated values.

      Dict = {} // {key=element} // {(keys),(elements)}

      Some methods that i usually use:
        - len(Dict)          lenght of dictionary
        - Dict.keys()        get all keys
        - Dict.value()       get all values
        - del Dict[key]
        - Dict.items()       tuples of key+value
```

#### Algorithms

-   Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
```python
# A simple function for generating first n numbers of Fibonacci Sequence

def fibonacci(n):
	sequence = [0,1]
	[sequence.append( sequence[i-1] +  sequence[i-2]) for i in range(2,n)]
	return  sequence
```

-   How do you find a max value in a list/array if you can’t use any built-in functions?
```python
# Like this:

def max_value(List = [None]):
	try:
		max = List[0]
		try:
			return max if max > max_value(List[1:])  else max_value(List[1:])
		except IndexError:
			return max

	except TypeError:
		return 'Something is not ok'
```

-   How do you find the average of values in a list/array if you can’t use any built-in functions?
```python
def sum(List = [0]):
	try:
		try:
			return List[0] + sum(List[1:])
		except IndexError:
			return List[0]

	except TypeError:
		raise TypeError

def average(List = [0]):
	try:
		return sum(List) / len(List)
	except TypeError:
		print('Ups...')
```

-   What do we call an *in-place* sort?
```
      An in-place algorithm is an algorithm that does not need an extra space and produces an output in the same memory that 
      contains the data by transforming the input ‘in-place’. However, a small constant extra space used for variables is allowed.
```

-   Explain an algorithm which sorts a list!
```python
def bubble_sort(List):
    # We set swapped to True so the loop looks runs at least once
    swapped = True
    while swapped:
        swapped = False
        for i in range(len(List) - 1):
            if List[i] > List[i + 1]:
                # Swap the elements
                List[i], List[i + 1] = List[i + 1], List[i]
                # Set the flag to True so we'll loop again
                swapped = True
```

#### Programming paradigms - procedural

-   What is the call stack?
```
      The call stack is what a program uses to keep track of method calls. The call stack is 
      made up of stack frames—one for each method call.
      A stack frame usually stores:
        - Local variables
        - Arguments passed into the method
        - Information about the caller's stack frame
        - The return address—what the program should do after the function returns (i.e.: where it should "return to")
```

-   What is “Stack overflow”?
```
      A stack overflow is an undesirable condition in which a particular computer program tries
      to use more memory space than the call stack has available.
```

-   What are the main parts of a function?
```
      A function is a device that groups a set of statements so they can be run more than once in a program
      — a packaged procedure invoked by name.

      A function definition consists the following components:
        - keyword *def* that marks the start of the function header
        - a function name to uniquely identify the function
        - parameters (arguments) through which we pass values to a function. They are optional
        - a colon (:) to mark the end of the function header
        - optional documentation string (docstring) to describe what the function does
        - one or more valid python statements that make up the function body; indentation level (usually 4 spaces)
        - an optional return statement to return a value from the function
```

#### Programming languages - Python  

-   How do you use a dictionary in Python?
```
      - create a new dictionary
      - add a value to the dictionary #the syntax is: mydict[key] = "value"
      - remove a key and it's value del mydict[key]
      - check the length print len(mydict)
      - get a value of a specified key
      - print mydict.get("key")
      ... and many more

      Basically you use dict when you need to associate values with keys, so you can look them up efficiently (by key) later on.
```

-   What does it mean that an object is immutable in Python?
```
      Simple put, a mutable object can be changed after it is created, and an immutable object can’t.

      mutable objects: list, dict, set, byte array
      immutable objects: int, float, complex, string, tuple, frozen set [note: immutable version of set], bytes
```

-   What is conditional expression in Python?
```python
# It allows for conditional execution of a statement or group of statements based on the value of an expression.

if <expr>:
    <statement>
elif <expr>:
    <statement>
else:
    <statement>
```

-   What are different types of arguments in Python?
```
        - default Argument - arguments can have default values
        - python Keyword Arguments - we can change the order of passing the arguments without any consequences
        - python Arbitrary Arguments - you may not always know how many arguments you’ll get
          -- in that case, you use an asterisk(*) before an argument name
```

-   What is variable shadowing? (context: variable scope)
```
      Variable shadowing is when a variable in a certain scope(eg., inside a loop) 
      has the same name as a variable declared in outer scope.
```
-   What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
```
      A lot of bad stuff if you are not carefull... basically once you change the list you, iterate a new one.
```

-   What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
```
      When local as well as global variable is present, preference is given to the local variable. Order followed is L>E>G>B.
      L = Local
      E = Enclosed (function is wrapped inside another function)
      G = Global
      B = Built-in
```

-   If you need to access the iterator variable after a for loop, how would you do it in Python?
```
      U save that iterator in another variable. cuz u know... it have just a short life lenght. poor guy...
```

-   What type of elements can a list contain in Python?
```
      Lists essentially store python objects and because everything in python is an object,
      then you can basically store anything in a list.
```

-   What is slice operator in Python and how to use?
```
        A slice operator is this little thing that helps you when u need to select or change data for a non.simple.numerical type.

        use like this
                  0      1      n-2    n-1
                  ['']   ['']...['']   ['']
                  -(n) -(n-1)     -2     -1
        [i:j:k] i,j - interval; k - step
```

-   What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
```
      +,* ...  they do fine (concatenate, repeat)  
```

-   What is the purpose of the in and not in membership operators in Python?
```
      in / not in - return a bool value(True or False) if one object is in or is not in a specified structure /another object
```

-   What does the + operator mean when used with strings in Python?
```
      What + do with strings? make a baby string (concatenate into a new object).
```

-   Explain f strings in Python?
```
      A New and Improved Way to Format Strings in Python!!!!

      old one:        '%s'%(str(object))
      the new one:    variable = (
                                   f"{variable_maybe}"
                                   f"{function_maybe()}"
                                 )
```

-   Name 4 iterable types in Python!
```
      Strings // Tuples // Lists // Sets // Dictionaries
```

-   What is the difference between list/set/dictionary comprehension and a generator expression in Python?
```
      list Comprehension - way of defining and creating a list
      generator Expressions - are somewhat similar to list comprehensions, but the former doesn’t construct
                              list object. Instead of creating a list and keeping the whole sequence in the memory,
                              the generator generates the next element in demand

            l = ['' for _ in range(n)]  # List comprehension
            g = ('' for _ in range(n))  # Generator expression
```

-   Does the order of the function definitions matter in Python? Why?
```
      It doesn't matter in which order the functions are created. It only matters when the call to the function is done.
      Ps. call after.  
```

-   What does unpacking mean in Python?
```
      Python has iterable assignment feature which enables you to assign more than one variable at a time.
      Packing and Unpacking of iterable.
      In packing, we place value into a new iterable while in unpacking we extract those values back into variables.
```

-   What happens when you try to assign the result of a function which has no return statement to a variable in Python?
```
      None happens! hahaha... ha...
```

## Software engineering

#### Debugging

-   What techniques can you use while debugging a program in Python?
```
      A quick and simple way of testing that a function is doing the right thing, for example,
      is to insert a print statement after every line which outputs the intermediate results.
      I just found pdb and loggin; i will look into it.
```

-   What does step over, step into and step out mean while using the debugger?
```
        (Step Into) A instruction is about to be invoked, and you want to debug into the code of that method,
                    so the next step is to go into that method and continue debugging step-by-step.
        (Step Over) A instruction is about to be invoked, but you're not interested in debugging this particular invocation,
                    so you want the debugger to execute that method completely as one entire step.
        (Step Out)  Step out proceeds until the next "return" or equivalent.
```

-   How can you start to debug a program from a certain line using the debugger?
```
      Get into "break mode" - run to a specific location or function, for example, by setting a breakpoint and starting your app.
```

#### Version control

-   What are the advantages of using a version control system?
```
      Why Use a Version Control System?
      Collaboration, Storing Versions (Properly), Restoring Previous Versions, Understanding What Happened, 
      Backup and Many More. Stay Tuned!!!
```

-   What is the difference between the working directory, the staging area and the repository in git?
```
      The working area aka the working tree - is like your scratch space, it's where you can add new content,
                                              you can modify delete content
      The staging area aka The cache or The index -  that's what files are going to be a part of your next commit.
                                                     It's how Git knows what is going to change between the current
                                                     commit and the next one
      The repository - contains all of your commits. And the commit is a snapshot of what your working and staging
                       area look like at the time of the commit

      All that is in your computer. Dont forget to push!!
```

-   What are remote repositories in git?
```
      A remote repositorie is Git's fancy way of saying "the place where code is stored."; where everyone who work on that
      project have access.
```

-   Why does a merge conflict occur?
```
      Conflicts generally arise when two people have changed the same lines in a file, or if one developer
      deleted a file while another developer was modifying it. In these cases, Git cannot automatically determine what is correct.
```

-   Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
```
      git add [file]
      git commit -m “[ Type in the commit message]”
      git push [variable name] [branch] [master]

      and  maybe - git status - for checking
```

-   What does it mean atomic commits and descriptive commit messages?
```
      Well. atomic commits... are atomic. Like small changes who work very well.
      Descriptive commit messages is a message who describe your changes. I think there are some rules for that.
```

-   What’s the difference between git and GitHub?
```
      Git is a version control system that lets you manage and keep track of your source code history.
      GitHub is a cloud-based hosting service that lets you manage Git repositories. If you have open-source projects that use Git,
      then GitHub is designed to help you better manage them.
```

## Software design

#### Clean code

-   What does clean code mean?
```
      I will be short. Be carefull  with naming, formatted code, repeated code, long method, wrong comments,
      and dead code... what is dead should not stay through living ones.
```

-   What steps do we usually do during a clean code refactoring?
```
      - checklist of refactoring done right way ;)
      - the code should become cleaner
      - new functionality shouldn’t be created during refactoring
      - all existing tests must pass after refactoring

      https://refactoring.guru/refactoring/smells - something fun
```

#### Error handling

-   What is exception handling?
```
      Exception handling is the process of responding to exceptions when a computer program runs.
      An exception occurs when an unexpected event happens that requires special processing.
```

-   What are the basics of exception handling in Python?
```python
#There are (at least) two distinguishable kinds of errors: syntax errors and exceptions.
#Syntax errors, also known as parsing errors, are perhaps the most common
#kind of complaint you get while you are still learning Python.
#Even if a statement or expression is syntactically correct, it may cause an error when
#an attempt is made to execute it.
#Errors detected during execution are called exceptions and are not unconditionally fatal.

      try:
          <statement>
      except <exception>:
          <statement>
      else:
          <statement>
      finally:
	        <statement>
```

-   In which case should we catch an exception? Why?
```
      In which case should we catch an exception? Sometimes, this isn’t what you want, though.
      You should catch the exception when you are in the method that knows what to do.
      An exception should be thrown when a function experiences a failure, i.e., an error.
```

-   What can/should we do with an exception in the ‘except’ block?
```
      You can jump to an exception handler in a single step, abandoning all function calls
      begun since the exception handler was entered.
      Code in the exception handler can then respond to the raised exception as appropriate:
          - Exception Roles
          - Error handling
          - Event notification
          - Special-case handling
          - Termination actions
          - Unusual control flows

      Python jumps to your handler—the block under the except clause that names
      the exception raised—automatically when an exception is triggered while the try block
      is running. The net effect is to wrap a nested block of code in an error handler that
      intercepts the block’s exceptions.
```

-   What does the else and finally statement do in a try-except block in Python?
```
      The purpose of the else clause is not always immediately obvious to Python newcomers.
      Without it, though, there is no direct way to tell (without setting and checking
      Boolean flags) whether the flow of control has proceeded past a try statement because
      no exception was raised, or because an exception occurred and was handled.

      The other flavor of the try statement is a specialization that has to do with finalization
      (a.k.a. termination) actions. If a finally clause is included in a try, Python will always
      run its block of statements “on the way out” of the try statement, whether an exception
      occurred while the try block was running or not.
```

## Software Development Methodologies

-   What is the main goal of a retrospective meeting?
```
      The purpose of the retrospective meeting is for the development team to discuss what went well during the
      just completed project and what did not. At this meeting, each team member should first answer those
      two questions as it pertains to him or her.
      The goal of the retrospective is for the team members to discuss among themselves about how the work went
      during the last project so that better ways can be found to meet the next project’s goals. This means the
      team should talk about its internal processes as well.

      Items for discussion might be:
          Can we improve our daily scrum meetings?
          Do we need to change any of the rules we are operating under?
          Is our communication with the Product Owner and stakeholders adequate?
          Are all stakeholders aware of our progress?
```

## Programming environment

#### Unix

-   What is UNIX and what is Linux?
```
      Unix is a complete operating system on the other hand Linux is just a kernel.
      Basically Linux is an engine(Just a kernel). // Unix is a Car. (Means Entire operating system).

      Ps. Most importantly Linux is GNU not Unix
```

-   What do we call the shell in Linux?
```
      Shell is an environment in which we can run our commands, programs, and shell scripts.
```

-   What does root means in a Linux environment?
```
      Root is the username or account that by default has access to all commands and files on a 
      Linux or other Unix-like operating system.
      It is also referred to as the root-account, root-user and the superuser.
```

-   How do you access your personal files in Linux?
```
      Well... is that a question? If u have GUI, is like in Windows: explore and click
      If not just type commands in shell. You will find your user-folder in /home/ussername/... and so on.
      cd ls nano and a lot more will help you.
```

-   How can you install an application in Linux?
```
      sudo apt-get install <package>
```

-   What is package management in Linux, what are repositories?
```
      A package manager or package-management system is a collection of software tools that automates
      the process of installing, upgrading, configuring, and removing computer programs for a computer's
      operating system in a consistent manner.

      like apt-get.

      A Linux repository is a storage location from which your system retrieves and installs OS updates and applications.
```

-   How do you navigate in the filesystem with the command line?
```
      cd path
```

-   What does the following commands do: mkdir, rm, cat, cp, touch?
```
      mkdir <name> - make folder
      rm <name> - remove file -a for folders
      cat - It is used to create the file with content
      cp - for copying files and directories
      touch - It is used to create a file without any content. The file created using touch command is empty
```

-   How can you look up what does a command do in Linux if you have no internet connection?
```
      to find the answer for this question use --help
```

-   What does the following commands do: head, tail, more, less?
```
      head - is a command-line utility for outputting the first part of files given to it via standard input
      more - is used to view the text files in the command prompt, displaying one screen at a time in case the file is large
      tail - is a command-line utility for outputting the last part of files given to it via standard input
      less - will open the file and display the file name at the lower left portion of the terminal
```

-   How do you download a file from internet using the terminal?
```
      try wget --options link
```
