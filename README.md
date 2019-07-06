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


### Common String Methods
#### Returns: 0 - true, 1 - false
| Method | Code | Comments |
| --- | --- | --- |
| Clone() | firstName.Clone() | Make clone of string |
| CompareTo() | firstName.CompareTo(lastname) | Compare two strings and returns integer value as output. It returns 0 for true and 1 for false |
| Contains | firstName.Contains("Dav") | The Contains method checks whether specified character or string is exists or not in the string value |
| EndsWith() | firstName.EndsWith("n") | This EndsWith Method checks whether specified character is the last character of string or not |
| Equals() | firstnName.Equals(lastname) | The Equals Method in C# compares two string and returns Boolean value as output |
| GetHashCode() | firstName.GetHashCode() | This method returns HashValue of specified string |
| GetType() | firstName.GetType() | Returns the System.Type of current instance |
| IndexOf() | firstName.IndexOf("e") | Returns the index position of first occurrence of specified character |
| ToLower() | firstName.ToLower() | Converts String into lower case based on rules of the current culture |
| ToUpper() | firstName.ToUper() | Converts String into upper case based on rules of the current culture |
| Insert() | firstName.Insert(0, "Hello") | Insert the string or character in the string at the specified position |
| IsNormalized() | firstName.IsNormalized() | This method checks whether this string is in Unicode normalization form C |
| LastIndexOf() | firsName.LastIndexOf("e") | This method checks whether this string is in Unicode normalization form C |
| Length | firstName.Length | It is a string property that returns length of string |
| Remove() | firstName.Remove(5) | This method deletes all the characters from beginning to specified index position |
| Replace() | firstName.Replace('e','i') | This method replaces the character |
| Split() | string[] split = firstname.Split(new char[] { 'e' }); | This method splits the string based on specified value |
| StartsWith() | firstName.StartsWith("S") | It checks whether the first character of string is same as specified character |
| Substring() | firstName.Substring(2,5) | This method returns substring |
| ToCharArray() | firstnName.ToCharArray() | Converts string into char array |
| Trim() | firstnName.Trim() | It removes extra whitespaces from beginning and ending of string |

### Parsing strings to convert them to DateTime objects 
```csharp
string dateInput = "Jan 1, 2009";
DateTime parsedDate = DateTime.Parse(dateInput);
Console.WriteLine(parsedDate);
// Displays the following output on a system whose culture is en-US:
//       1/1/2009 12:00:00 AM
```
You can read more about Parsing strings to convert them to DateTime objects [here](https://docs.microsoft.com/en-us/dotnet/standard/base-types/parsing-datetime#code-try-0) 

In C#, the string keyword is an alias for [String](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=netframework-4.8). Therefore, String and string are equivalent, and you can use whichever naming convention you prefer. 


