# C-sharp-Cheatsheet
A cheat sheet to the C# language/ All-in-One / Still Editing
![paM5iAD](https://user-images.githubusercontent.com/33767811/60687870-77aa3c00-9ec2-11e9-8db7-a78cd60569eb.jpg)

- **[String](#String)**
- **[DateTime](#DateTime)**
- **[Exception class](#Complete-List-Of-Exception-Class-In-C#)**

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

## DateTime

DateTime is a structure of value Type like int, double etc. It is available in System namespace and present in mscorlib.dll assembly. It implements interfaces like IComparable, IFormattable, IConvertible, ISerializable, IComparable, IEquatable. 
```csharp
public struct DateTime : IComparable, IFormattable, IConvertible, ISerializable, IComparable<DateTime>, IEquatable<DateTime>
{
    // Contains methods and properties  
}
```
DateTime helps developer to find out more information about Date and Time like Get month, day, year, week day. It also helps to find date difference, add number of days to a date, etc.

### Standard DateTime Formatting
DateTimeFormatInfo specifies a set of specifiers for simple date and time formatting. Every specifier correspond to
a particular DateTimeFormatInfo format pattern.
```csarp
//Create datetime
DateTime dt = new DateTime(2016, 08, 01, 18, 50, 23, 230);
var t = String.Format("{0:t}", dt);     // "6:50 PM" ShortTime
var d = String.Format("{0:d}", dt);     // "8/1/2016" ShortDate
var T = String.Format("{0:T}", dt);     // "6:50:23 PM" LongTime
var D = String.Format("{0:D}", dt);     // "Monday, August 1, 2016" LongDate
var f = String.Format("{0:f}", dt);     // "Monday, August 1, 2016 6:50 PM" LongDate+ShortTime
var F = String.Format("{0:F}", dt);     // "Monday, August 1, 2016 6:50:23 PM" FullDateTime
var g = String.Format("{0:g}", dt);     // "8/1/2016 6:50 PM" ShortDate+ShortTime
var G = String.Format("{0:G}", dt);     // "8/1/2016 6:50:23 PM" ShortDate+LongTime
var m = String.Format("{0:m}", dt);     // "August 1" MonthDay
var y = String.Format("{0:y}", dt);     // "August 2016" YearMonth
var r = String.Format("{0:r}", dt);     // "SMon, 01 Aug 2016 18:50:23 GMT" RFC1123
var s = String.Format("{0:s}", dt);     // "2016-08-01T18:50:23" SortableDateTime
var u = String.Format("{0:u}", dt);     // "2016-08-01 18:50:23Z" UniversalSortableDateTime
```
#### Custom DateTime Formatting
There are following custom format specifiers:
-y (year)
-M (month)
-d (day)
-h (hour 12)
-H (hour 24)
-m (minute)
-s (second)
-f (second fraction)
-F (second fraction, trailing zeroes are trimmed)
-t (P.M or A.M)
-z (time zone)

```csharp
var year = String.Format("{0:y yy yyy yyyy}", dt);      // "16 16 2016 2016" year
var month = String.Format("{0:M MM MMM MMMM}", dt);     // "8 08 Aug August" month
var day = String.Format("{0:d dd ddd dddd}", dt);       // "1 01 Mon Monday" day
var hour = String.Format("{0:h hh H HH}", dt);          // "6 06 18 18" hour 12/24
var minute = String.Format("{0:m mm}", dt);             // "50 50" minute
var secound = String.Format("{0:s ss}", dt);            // "23 23" second
var fraction = String.Format("{0:f ff fff ffff}", dt);  // "2 23 230 2300" sec.fraction
var fraction2 = String.Format("{0:F FF FFF FFFF}", dt); // "2 23 23 23" without zeroes
var period = String.Format("{0:t tt}", dt);             // "P PM" A.M. or P.M.
var zone = String.Format("{0:z zz zzz}", dt);           // "+0 +00 +00:00" time zone
```
### DateTime Formatting

Different users need different kinds of  format date. For instance some users need date like "mm/dd/yyyy", some need "dd-mm-yyyy". Let's say current Date Time is "12/8/2015 3:15:19 PM" and as per specifier you will get below output.
```csharp
DateTime tempDate = new DateTime(2015, 12, 08);         // creating date object with 8th December 2015  
Console.WriteLine(tempDate.ToString("MMMM dd, yyyy"));  //December 08, 2105.  
```
Below specifiers will help you to get the date in different formats.

| Specifier | Description | Output |
| --- | --- | --- |
| d | Short Date |	12/8/2015 |
| D | Long Date |	Tuesday, December 08, 2015 |
| t | Short Time |	3:15 PM |
| T | Long Time |	3:15:19 PM |
| f | Full date and time |	Tuesday, December 08, 2015 3:15 PM |
| F | Full date and time (long) |	Tuesday, December 08, 2015 3:15:19 PM |
| g | Default date and time |	12/8/2015 15:15 |
| G | Default date and time (long) |	12/8/2015 15:15 |
| M | Day / Month |	8-Dec |
| r | RFC1123 date |	Tue, 08 Dec 2015 15:15:19 GMT |
| s | Sortable date/time |	2015-12-08T15:15:19 |
| u | Universal time, local timezone |	2015-12-08 15:15:19Z |
| Y | Month / Year |	December, 2015 |
| dd | Day | 8 |
| ddd |	Short Day Name | Tue |
| dddd |	Full Day Name |	Tuesday |
| hh | 2 digit hour | 3 |
| HH | 2 digit hour (24 hour) | 15 |
| mm | 2 digit minute | 15 |
| MM | Month |	12|
| MMM | Short Month name | Dec |
| MMMM | Month name | December |
| ss | seconds | 19 |
| fff |	milliseconds | 120 |
| FFF |	milliseconds without trailing zero | 12 |
| tt | AM/PM | PM |
| yy | 2 digit year | 15 |
| yyyy |	4 digit year| 2015 |
| : | Hours, minutes, seconds separator, e.g. {0:hh:mm:ss} | 9:08:59 |
| / | Year, month , day separator, e.g. {0:dd/MM/yyyy} | 8/4/2007 |

### DateTime Parsing

Sometimes we do parsing from string to DateTime object to perform operations like date difference, weekday, month name etc. For instance, there is a string value (“12/10/2015”) and our requirement is to find out weekday (Sunday or Monday and so on) of date. In this scenario we need to convert string value to DateTime object and then use WeekDay property(obj.WeekDay) to find out weekday. We can accomplish the same by built-in methods like Convert.ToDateTime(), DateTime.Parse(), DateTime.ParseExact(), DateTime.TryParse(), DateTime.TryParseExact(). Here are a few examples of how to parse a string to DateTime object:

#### ParseExact
```csharp
var dateString = "2015-11-24";
var date = DateTime.ParseExact(dateString, "yyyy-MM-dd", null);
Console.WriteLine(date);  //11/24/2015 12:00:00 AM
```
Note that passing CultureInfo.CurrentCulture as the third parameter is identical to passing null. Or, you can
pass a specific culture. Input string can be in any format that matches the format string.
```csharp
var date = DateTime.ParseExact("24|201511", "dd|yyyyMM", null);
Console.WriteLine(date);  //11/24/2015 12:00:00 AM

//Case matters for format specifiers
var date = DateTime.ParseExact("2015-01-24 11:11:30", "yyyy-mm-dd hh:MM:ss", null);
Console.WriteLine(date);    //11/24/2015 11:01:30 AM
```
Note that the month and minute values were parsed into the wrong destinations.

#### TryParse
This method accepts a string as input, attempts to parse it into a DateTime, and returns a Boolean result indicating
success or failure. If the call succeeds, the variable passed as the out parameter is populated with the parsed result.
If the parse fails, the variable passed as the out parameter is set to the default value, DateTime.MinValue.
TryParse(string, out DateTime)
```csharp
DateTime parsedValue;
if (DateTime.TryParse("monkey", out parsedValue))
{
    Console.WriteLine("Apparently, 'monkey' is a date/time value. Who knew?");
}
```
This method attempts to parse the input string based on the system regional settings and known formats such as ISO 8601 and other common formats.
```csharp
DateTime.TryParse("11/24/2015 14:28:42", out parsedValue);       // true
DateTime.TryParse("2015-11-24 14:28:42", out parsedValue);       // true
DateTime.TryParse("2015-11-24T14:28:42", out parsedValue);       // true
DateTime.TryParse("Sat, 24 Nov 2015 14:28:42", out parsedValue); // true
```
TryParse(string, IFormatProvider, DateTimeStyles, out DateTime)

```csharp
if (DateTime.TryParse(" monkey ", new CultureInfo("en-GB"),
 DateTimeStyles.AllowLeadingWhite | DateTimeStyles.AllowTrailingWhite, out parsedValue)
{
    Console.WriteLine("Apparently, ' monkey ' is a date/time value. Who knew?");
}
```
Unlike its sibling method, this overload allows a specific culture and style(s) to be specified. Passing **null** for the
**IFormatProvider** parameter uses the system culture.

Exceptions

Note that it is possible for this method to throw an exception under certain conditions. These relate to the
parameters introduced for this overload: **IFormatProvider** and **DateTimeStyles**.
- `NotSupportedException`: `IFormatProvider` specifies a neutral culture
- `ArgumentException`: `DateTimeStyles` is not a valid option, or contains incompatible flags such as
  `AssumeLocal` and `AssumeUniversal`.

#### TryParseExact

This method behaves as a combination of TryParse and ParseExact: It allows custom format(s) to be specified, and returns a Boolean result indicating success or failure rather than throwing an exception if the parse fails.
**TryParseExact(string, string, IFormatProvider, DateTimeStyles, out DateTime)**
This overload attempts to parse the input string against a specific format. The input string must match that format in order to be parsed.
```csharp
DateTime.TryParseExact("11242015", "MMddyyyy", null, DateTimeStyles.None, out parsedValue); // true
```
**TryParseExact(string, string[], IFormatProvider, DateTimeStyles, out DateTime)**
This overload attempts to parse the input string against an array of formats. The input string must match at least
one format in order to be parsed.
```csharp
DateTime.TryParseExact("11242015", new [] { "yyyy-MM-dd", "MMddyyyy" }, null, DateTimeStyles.None, out parsedValue); // true
```

Now a question arises in your mind, that is, why do we have so many methods for parsing? The reason is every method is for a different purpose. Use TryParse() when you want to be able to attempt a parse and handle invalid data immediately (instead of throwing the exception), and ParseExact() when the format you are expecting is not a standard format, or when you want to limit to one particular standard format for efficiency. If you're sure the string is a valid DateTime, and you know the format, you could also consider the DateTime.ParseExact() or DateTime.TryParseExact() methods.

For more methods click this [link](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?redirectedfrom=MSDN&view=netframework-4.8#methods).

For more information about DateTime click these [link](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?redirectedfrom=MSDN&view=netframework-4.8#constructors)

#### Pure functions warning when dealing with DateTime

Wikipedia currently defines a pure function as follows:

1. The function always evaluates the same result value given the same argument value(s). The function result
value cannot depend on any hidden information or state that may change while program execution proceeds
or between different executions of the program, nor can it depend on any external input from I/O devices .

2. Evaluation of the result does not cause any semantically observable side effect or output, such as mutation
of mutable objects or output to I/O devices
As a developer you need to be aware of pure methods and you will stumble upon these a lot in many areas. One I
have seen that bites many junior developers is working with DateTime class methods. A lot of these are pure and if
you are unaware of these you can be in for a suprise. An example:
```csharp
DateTime sample = new DateTime(2016, 12, 25);
sample.AddDays(1);
Console.WriteLine(sample.ToShortDateString());
```
Given the example above one may expect the result printed to console to be '26/12/2016' but in reality you end up with the same date. This is because AddDays is a pure method and does not affect the original date. To get the expected output you would have to modify the AddDays call to the following:
```csharp
sample = sample.AddDays(1)
```

## Complete List Of Exception Class In C#

#### WHAT IS SYSTEM EXCEPTION?
System Exception is predefined Exception class in C# that is ready to use in programming. Just choose which exception may occur in your code and use it in a catch block. You can use this exception for writing error free and robust code.

#### System Exception
| Exception| Condition |
| --- | --- | 
| AccessViolationException | It is thrown when try to read or write protected memory. |
| AggregateException | Represents one or more errors that occur during application execution. |
| AppDomainUnloadedException | It is thrown when try to access an unloaded application domain. |
| ApplicationException | It is base class for application-defined exceptions. |
| ArgumentException | It is thrown when invalid argument provided to a method.|
| ArgumentNullException | It is thrown when a method requires argument but no argument is provided.|
| ArgumentOutOfRangeException |	It is thrown when value of an argument is outside the allowable range.|
| ArithmeticException |	It is thrown when doing arithmetic, casting, or conversion operation.|
| ArrayTypeMismatchException | It is thrown when try to store an element of the wrong type within an array.|
| BadImageFormatException |	It is thrown when file image, dll or exe program is invalid.|
| CannotUnloadAppDomainException | It is thrown when try to unload an application domain fails.|
| ContextMarshalException |	The exception that is thrown when an attempt to marshal an object across a context boundary fails.|
|DataMisalignedException|It is thrown thrown when a unit of data is read from or written to an address that is not a multiple of the data size.|
|DivideByZeroException|	It is thrown when there is an attempt to divide an integral or decimal value by zero.|
|DllNotFoundException|	It is thrown when a DLL specified in a DLL import cannot be found.|
|DuplicateWaitObjectException|	The exception that is thrown when an object appears more than once in an array of synchronization objects.
|EntryPointNotFoundException|	The exception that is thrown when an attempt to load a class fails due to the absence of an entry method.|
|ExecutionEngineException|	The exception that is thrown when there is an internal error in the execution engine of the common language runtime.|
|FieldAccessException|	It is thrown when there is an invalid attempt to access a private or protected field inside a class.|
|FormatException|	The exception that is thrown when the format of an argument is invalid, or when a composite format string is not well formed.|
|IndexOutOfRangeException|	The exception that is thrown when an attempt is made to access an element of an array or collection with an index that is outside its bounds.|
|InsufficientMemoryException|	The exception that is thrown when a check for sufficient available memory fails. This class cannot be inherited.|
|InvalidCastException|	The exception that is thrown for invalid casting or explicit conversion.|
|InvalidOperationException|	The exception that is thrown when a method call is invalid for the object's current state.|
|InvalidProgramException|	The exception that is thrown when a program contains invalid Microsoft intermediate language (MSIL) or metadata.|
|InvalidTimeZoneException|	The exception that is thrown when time zone information is invalid.|
|MemberAccessException|	The exception that is thrown when an attempt to access a class member fails.|
|MethodAccessException|	The exception that is thrown when there is an invalid attempt to access a method, such as accessing a private method from partially trusted code.|
|MissingFieldException|	The exception that is thrown when there is an attempt to dynamically access a field that does not exist.|
|MissingMemberException	|The exception that is thrown when there is an attempt to dynamically access a class member that does not exist.|
|MissingMethodException	|The exception that is thrown when there is an attempt to dynamically access a method that does not exist.|
|MulticastNotSupportedException|	The exception that is thrown when there is an attempt to combine two delegates based on the Delegate type instead of the MulticastDelegate type.|
|NotCancelableException	|It is thrown when an attempt is made to cancel an operation that is not cancelable.|
|NotFiniteNumberException|	The exception that is thrown when a floating-point value is positive infinity, negative infinity, or Not-a-Number (NaN).|
|NotImplementedException|	The exception that is thrown when a requested method or operation is not implemented.|
|NotSupportedException|	The exception that is thrown when an invoked method is not supported, or when there is an attempt to read, seek, or write to a stream that does not support the invoked functionality.|
|NullReferenceException|	The exception that is thrown when there is an attempt to dereference a null object reference.|
|ObjectDisposedException|	The exception that is thrown when an operation is performed on a disposed object.|
|OperationCanceledException|	The exception that is thrown in a thread upon cancellation of an operation that the thread was executing.|
|OutOfMemoryException|	The exception that is thrown when there is not enough memory to continue the execution of a program.|
|OverflowException	|The exception that is thrown when an arithmetic, casting, or conversion operation in a checked context results in an overflow.|
|PlatformNotSupportedException|	The exception that is thrown when a feature does not run on a particular platform.|
|RankException	|The exception that is thrown when an array with the wrong number of dimensions is passed to a method.|
|StackOverflowException|	The exception that is thrown when the execution stack overflows because it contains too many nested method calls.|
|SystemException|	Serves as the base class for system exceptions namespace.|
|TimeoutException|	The exception that is thrown when the time allotted for a process or operation has expired.|
|TimeZoneNotFoundException|	The exception that is thrown when a time zone cannot be found.|
|TypeAccessException	|The exception that is thrown when a method attempts to use a type that it does not have access to.|
|TypeInitializationException|	The exception that is thrown as a wrapper around the exception thrown by the class initializer. This class cannot be inherited.|
|TypeLoadException	|The exception that is thrown when type-loading failures occur.|
|TypeUnloadedException|	The exception that is thrown when there is an attempt to access an unloaded class.|
|UnauthorizedAccessException|	The exception that is thrown when the operating system denies access because of an I/O error or a specific type of security error.|
|UriFormatException|The exception that is thrown when an invalid Uniform Resource Identifier (URI) is detected.|
#### System.Data Exception
| Exception| Condition |
| --- | --- | 
|ConstraintException|	Represents the exception that is thrown when attempting an action that violates a constraint.|
|DataException|	Represents the exception that is thrown when attempting an action that violates a constraint.|
|DBConcurrencyException	|Gets or sets the value of the DataRow that generated the DBConcurrencyException.|
|DeleteRowInaccessibleException|	Represents the exception that is thrown when an action is tried on a DataRow that has been deleted.|
|DuplicateNameException|	Represents the exception that is thrown when a duplicate database object name is encountered during an add operation in a DataSet -related object.|
|EvaluateException|	Represents the exception that is thrown when the Expression property of a DataColumn cannot be evaluated.|
|InRowChangingEventException|	Represents the exception that is thrown when you call the EndEdit method within the RowChanging event.|
|InvalidConstraintException|	Represents the exception that is thrown when incorrectly trying to create or access a relation.|
|InvalidExpressionException	|Represents the exception that is thrown when you try to add a DataColumn that contains an invalid Expression to a DataColumnCollection.|
|MissingPrimaryKeyException|	Represents the exception that is thrown when you try to access a row in a table that has no primary key.|
|NoNullAllowedException|	Represents the exception that is thrown when you try to insert a null value into a column where AllowDBNull is set tofalse.|
|OperationAbortedException|	This exception is thrown when an ongoing operation is aborted by the user.|
|ReadOnlyException|	Represents the exception that is thrown when you try to change the value of a read-only column.|
|RowNotInTableException|	Represents the exception that is thrown when you try to perform an operation on a DataRow that is not in a DataTable.|
|StrongTypingException|	The exception that is thrown by a strongly typed DataSet when the user accesses a DBNull value.|
|SyntaxErrorException	|Represents the exception that is thrown when the Expression property of a DataColumn contains a syntax error.|
|TypedDataSetGeneratorException|	The exception that is thrown when a name conflict occurs while generating a strongly typed DataSet.|
|VersionNotFoundException|	Represents the exception that is thrown when you try to return a version of a DataRow that has been deleted.|
#### System.IO Exception
| Exception| Condition |
| --- | --- | 
|DirectoryNotFoundException|	The exception that is thrown when part of a file or directory cannot be found.|
|DriveNotFoundException|	The exception that is thrown when a drive that is referenced by an operation could not be found.|
|EndOfStreamException|	An EndOfStreamException exception is thrown when there is an attempt to read past the end of a stream.|
|FileFormatException|	The exception that is thrown when an input file or a data stream that is supposed to conform to a certain file format specification is malformed.|
|FileLoadException|	The exception that is thrown when a managed assembly is found but cannot be loaded.|
|FileNotFoundException|	The exception that is thrown when an attempt to access a file that does not exist on disk fails.|
|InternalBufferOverflowException|	The exception thrown when the internal buffer overflows.|
|InvalidDataException|	The exception that is thrown when a data stream is in an invalid format.|
|IOException|	The exception that is thrown when an I/O error occurs.|
|PathTooLongException|	The exception that is thrown when a path or file name is longer than the system-defined maximum length.|
|PipeException|	Thrown when an error occurs within a named pipe.|
