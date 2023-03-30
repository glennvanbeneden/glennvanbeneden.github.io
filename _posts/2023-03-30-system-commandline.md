---
title: Using Microsoft's commandline utility package
category: development
---

As I was experimenting with trying to write a CLI application using a Command Line Parser, I stumbled on Microsoft's System.CommandLine package.
This package is currently in prerelease and can be added with the following command.

Let's start with a simple program

```csharp
var command = new RootCommand();
var nameOption = new Option<string>("--name", "The name of the person to greet.");
command.Add(nameOption);
command.SetHandler(name => Console.WriteLine($"Hello, {name}") , nameOption);
command.InvokeAsync(args);
```

The first thing you got to do is define a root command

``` csharp
var rootCommand = new RootCommand();
```

Under the root command you have several methods to add an argument, an option, a command, ... however you can simply use the `Add()` method which takes any of the types as an argument.
Since we want to provide a name as an option we need to define it and add it as part of the root command in our case. However if you want to provide it as an option to one of your subcommand, you need to add it to that command in particular.

To assign a handler function to a particular command, we use the SetHandler function, which expects an Action delegate as its argument. We also pass in an option as the second argument, so that we can use the value of the option as an input parameter to the handler function.

Last but not least, we need to use the `InvokeAsync()` method on the root command to start using the parser

# What's the difference between an option and an argument?
When working with command-line interfaces (CLI), it's important to understand the difference between options and arguments. Both options and arguments are used to provide additional information to a command, but they have different purposes and usage.

An option is a command-line flag that modifies the behavior of a command. Options typically start with a hyphen (-) or two hyphens (--), followed by a short or long name. For example, in the command ls -l, the -l option tells the ls command to display the output in long format. Options can be used to enable or disable certain features, set configuration parameters, or specify input or output options.

Options can also have arguments associated with them. An argument is a value that follows an option and provides additional information to the command. For example, in the command grep -i hello file.txt, the -i option tells the grep command to perform a case-insensitive search, and the hello argument specifies the search pattern. In some cases, options can take multiple arguments, separated by commas or spaces.

On the other hand, an argument is a value that specifies the target of a command or operation. Arguments typically come after the command and options and can be positional or named. Positional arguments are specified by their position in the command line, while named arguments are specified by their name or a keyword. For example, in the command git commit -m "Add new feature", the commit command takes a positional argument that specifies the action to perform, and the -m option takes a named argument that specifies the commit message.