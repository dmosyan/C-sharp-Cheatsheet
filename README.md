# C-sharp-Cheatsheet
A cheat sheet to the C# language/ All-in-One / Still Editing
![paM5iAD](https://user-images.githubusercontent.com/33767811/60687870-77aa3c00-9ec2-11e9-8db7-a78cd60569eb.jpg)



## String
The string is a sequence of characters surrounded with double quotes. A string class in C# is an object of type System.String. The String class in C# represents a string.
String class defined in the .NET base class library represents text as a series of Unicode characters. The String class provides methods and properties to work with strings.

The String class has methods to clone a string, compare strings, concatenate strings, and copy strings. This class also provides methods to find a substring in a string, find the index of a character or substring, replace characters, split a string, trim a string, and add padding to a string.
The string class also provides methods to convert a string's characters to uppercase or lowercase.
```csharp
string firstName = "David";
string lastName = "Mosyan";
```

### Concatenating
To concatenate string variables, you can use the 
**+** or **+=** operators, **string interpolation** or **the String.Format, String.Concat, String.Join** or **StringBuilder.Append** methods. 
The + operator is easy to use and makes for intuitive code. Even if you use several + operators in one statement, the string content is copied only once.
The following code shows examples of using the + and += operators to concatenate strings:

```csharp
string fullName = firstName + " " + lastName; // + operator
string fullName = string fullName = string.Format("{0} {1}", firstName, lastName); // .Format method
string fullName = $"My name is {firstName} and my last name is {lastName}."; // Interpolation

string[] words = { "The", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog." };
string unreadablePhrase = string.Concat(words);
Console.WriteLine(unreadablePhrase); //The output is " Thequickbrownfoxjumpsoverthelazydog. "
```
Use **String.Join** method if source strings should be separated by a delimeter.
```csharp
string[] words = { "The", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog." };
string readablePhrase = string.Join(" ", words);
Console.WriteLine(readablePhrase); // The output is " The quick brown fox jumps over the lazy dog. "
```
In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining,
and the actual number of source strings may be quite large. The **StringBuilder** class was designed for these scenarios.
The following code uses the **Append** method of the **StringBuilder** class to concatenate strings.

```csharp
var sb = new System.Text.StringBuilder();
for (int i = 0; i < 20; i++)
{
    sb.AppendLine(i.ToString());
}
Console.WriteLine(sb.ToString());
```
You can read more about the [reasons to choose string concatenation or the StringBuilder class](https://docs.microsoft.com/en-us/dotnet/api/system.text.stringbuilder?view=netframework-4.8#StringAndSB) 

