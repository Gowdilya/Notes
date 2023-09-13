In C#, a StringBuilder is a mutable series of characters that can be extended to store more characters if required. Unlike with strings, modifying a StringBuilder instance does not result in the creation of a new instance in memory.
```c#
[Benchmark]  
    public string StringConcatenationUsingStringBuilder()  
        {  
            StringBuilder stringBuilder = new StringBuilder();  
            for (int i = 0; i < NumberOfRuns; i++)  
            {  
                stringBuilder.AppendLine("Hello World" + i);  
            }  
            return stringBuilder.ToString();  
        }  
[Benchmark]  
    public string StringConcatenationUsingString()  
        {  
            string str = null;  
            for (int i = 0; i < NumberOfRuns; i++)  
            {  
                str += "Hello World" + i;  
            }  
            return str;  
        }
```

As you can see in Figure 1, concatenating strings using StringBuilder is much faster, consumes much less memory, and uses fewer garbage collections in all generations, compared to using the ‘+’ operator to combine two or more strings.

Note that regular string concatenations are faster than using the StringBuilder but only when you’re using a few of them at a time. If you are using two or three string concatenations, use a string. StringBuilder will improve performance in cases where you make repeated modifications to a string or concatenate many strings together.

In short, use StringBuilder only for a large number of concatenations.