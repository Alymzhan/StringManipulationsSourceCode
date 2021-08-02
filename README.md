# C# String manipulations SourceCode
List of String manipulations methods for C#. Examples were provided by Tim Corey.
I added output results under each example as comment. 

 ## String Conversion
```c#

            string testString = "tHis iS tHe FBI Calling!";
            TextInfo currentTextInfo = CultureInfo.CurrentCulture.TextInfo;
            TextInfo englishTextInfo = new CultureInfo("en-US", false).TextInfo;
            string result;

            result = testString.ToLower();
            Console.WriteLine(result);
            //this is the fbi calling!

            result = testString.ToUpper();
            Console.WriteLine(result);
            //THIS IS THE FBI CALLING!

            result = englishTextInfo.ToTitleCase(testString);
            Console.WriteLine(result);
            //This Is The FBI Calling!
        
```

## String as Array
```c#

            string testString = "Timothy";

            for (int i = 0; i < testString.Length; i++)
            {
                Console.WriteLine(testString[i]);
            }
            /*
                T
                i
                m
                o
                t
                h
                y
            */
        
```

## Escape String
```c#

            string results;

            results = "This is my \"test\" solution.";
            Console.WriteLine(results);
            //This is my "test" solution.

            results = "C:\\Demo\\Test.txt";
            Console.WriteLine(results);
            //C:\Demo\Test.txt

            results = @"C:\Demo\Test.txt";
            Console.WriteLine(results);
            //C:\Demo\Test.txt
        
```

## Appending Strings
```c#

            string firstName = "Tim";
            string lastName = "Corey";
            string results;

            results = firstName + ", my name is " + firstName + " " + lastName;
            Console.WriteLine(results);
            //Tim, my name is Tim Corey

            results = string.Format("{0}, my name is {0} {1}", firstName, lastName);
            Console.WriteLine("{0}, my name is {0} {1}", firstName, lastName);
            //Tim, my name is Tim Corey
            Console.WriteLine(results);
            //Tim, my name is Tim Corey

            results = $"{firstName}, my name is {firstName} {lastName}";
            Console.WriteLine(results);
            //Tim, my name is Tim Corey
        
```

## Interpolation and Literal
```c#

            string testString = "Tim Corey";
            string results = $@"C:\Demo\{testString}\{"\""}Test{"\""}.txt";

            Console.WriteLine(results);
            //C:\Demo\Tim Corey\"Test".txt
        
```

## StringBuilder Demo
```c#

            Stopwatch regularStopwatch = new Stopwatch();
            regularStopwatch.Start();

            string test = "";

            for (int i = 0; i < 100000; i++)
            {
                test += i;
            }

            regularStopwatch.Stop();
            Console.WriteLine($"Regular Stopwatch: { regularStopwatch.ElapsedMilliseconds }ms");
            //Regular Stopwatch: 16980ms

            Stopwatch builderStopwatch = new Stopwatch();
            builderStopwatch.Start();

            StringBuilder sb = new();

            for (int i = 0; i < 100000; i++)
            {
                sb.Append(i);
            }
            
            builderStopwatch.Stop();
            Console.WriteLine($"String Builder Stopwatch: { builderStopwatch.ElapsedMilliseconds }ms");
            //String Builder Stopwatch: 4ms
        
```

## Working with Arrays
```c#

            int[] ages = new int[] { 6, 7, 8, 3, 5 };
            string results;

            results = String.Concat(ages);
            Console.WriteLine(results);
            //67835

            results = String.Join(",", ages);
            Console.WriteLine(results);
            //6,7,8,3,5

            Console.WriteLine();

            string testString = "Jon,Tim,Mary,Sue,Bob,Jane";
            string[] resultsArray = testString.Split(',');

            Array.ForEach(resultsArray, x => Console.WriteLine(x));

            Console.WriteLine();
            /*
                Jon
                Tim
                Mary
                Sue
                Bob
                Jane
            */

            testString = "Jon, Tim, Mary, Sue, Bob, Jane";
            resultsArray = testString.Split(", ");

            Array.ForEach(resultsArray, x => Console.WriteLine(x));
            /*
                Jon
                Tim
                Mary
                Sue
                Bob
                Jane
            */
            
        
```

## Pad and Trim
```c#

            string testString = "     Hello World      ";
            string results;

            results = testString.TrimStart();
            Console.WriteLine($"'{results}'");
            //'Hello World      '

            results = testString.TrimEnd();
            Console.WriteLine($"'{results}'");
            //'     Hello World'

            results = testString.Trim();
            Console.WriteLine($"'{results}'");
            //'Hello World'

            testString = "1.15";

            results = testString.PadLeft(10, '0');
            Console.WriteLine(results);
            //0000001.15

            results = testString.PadRight(10, '0');
            Console.WriteLine(results);
            //1.15000000
        
```

## Searching Strings
```c#

            string testString = "This is a test of the search. Let's see how its testing works out.";
            bool resultsBoolean;
            int resultsInt;

            resultsBoolean = testString.StartsWith("This is");
            Console.WriteLine($"Starts with \"This is\": {resultsBoolean}");
            //Starts with "This is": True

            resultsBoolean = testString.StartsWith("ThIs is");
            Console.WriteLine($"Starts with \"ThIs is\": {resultsBoolean}");
            //Starts with "ThIs is": False

            resultsBoolean = testString.EndsWith("works out.");
            Console.WriteLine($"Ends with \"works out.\": {resultsBoolean}");
            //Ends with "works out.": True

            resultsBoolean = testString.EndsWith("work out.");
            Console.WriteLine($"Ends with \"work out.\": {resultsBoolean}");
            //Ends with "work out.": False

            resultsBoolean = testString.Contains("test");
            Console.WriteLine($"Contains \"test\": {resultsBoolean}");
            //Contains "test": True

            resultsBoolean = testString.Contains("tests");
            Console.WriteLine($"Contains \"tests\": {resultsBoolean}");
            //Contains "tests": False

            resultsInt = testString.IndexOf("test");
            Console.WriteLine($"Index of \"test\": {resultsInt}");
            //Index of "test": 10

            resultsInt = testString.IndexOf("test", 11);
            Console.WriteLine($"Index of \"test\" after character 10: {resultsInt}");
            //Index of "test" after character 10: 48

            resultsInt = testString.IndexOf("test", 49);
            Console.WriteLine($"Index of \"test\" after character 48: {resultsInt}");
            //Index of "test" after character 48: -1

            resultsInt = testString.LastIndexOf("test");
            Console.WriteLine($"Last Index of \"test\": {resultsInt}");
            //Last Index of "test": 48

            resultsInt = testString.LastIndexOf("test", 48);
            Console.WriteLine($"Last Index of \"test\" before character 48: {resultsInt}");
            //Last Index of "test" before character 48: 10

            resultsInt = testString.LastIndexOf("test", 10);
            Console.WriteLine($"Last Index of \"test\" before character 10: {resultsInt}");
            //Last Index of "test" before character 10: -1
        
```

## Ordering Strings
```c#

            CompareToHelper("Mary", "Bob");
            //CompareTo: Bob comes before Mary
            CompareToHelper("Mary", null);
            //CompareTo: null comes before Mary
            CompareToHelper("Adam", "Bob");
            //CompareTo: Adam comes before Bob
            CompareToHelper("Bob", "Bob");
            //CompareTo: Bob is the same as Bob
            CompareToHelper("Bob", "Bobby");
            //CompareTo: Bob comes before Bobby

            Console.WriteLine();

            CompareHelper("Mary", "Bob");
            //Compare: Bob comes before Mary
            CompareHelper("Mary", null);
            //Compare: null comes before Mary
            CompareHelper(null, "Bob");
            //Compare: null comes before Bob
            CompareHelper("Adam", "Bob");
            //Compare: Adam comes before Bob
            CompareHelper("Bob", "Bob");
            //Compare: Bob is the same as Bob
            CompareHelper("Bob", "Bobby");
            //Compare: Bob comes before Bobby
            CompareHelper(null, null);
            //Compare: null is the same as null

        
            public static void CompareToHelper(string testA, string? testB)
            {
                int resultsInt = testA.CompareTo(testB);
                switch (resultsInt)
                {
                    case > 0:
                        Console.WriteLine($"CompareTo: { testB ?? "null" } comes before { testA }");
                        break;
                    case < 0:
                        Console.WriteLine($"CompareTo: { testA } comes before { testB }");
                        break;
                    case 0:
                        Console.WriteLine($"CompareTo: { testA } is the same as { testB }");
                        break;
                }
            }

            public  static void  CompareHelper(string? testA, string? testB)
            {
                int resultsInt = String.Compare(testA, testB);

                switch (resultsInt)
                {
                    case > 0:
                        Console.WriteLine($"Compare: { testB ?? "null" } comes before { testA }");
                        break;
                    case < 0:
                        Console.WriteLine($"Compare: { testA ?? "null" } comes before { testB }");
                        break;
                    case 0:
                        Console.WriteLine($"Compare: { testA ?? "null" } is the same as { testB ?? "null" }");
                        break;
                }
            }

```

## Testing Equality
```c#

            EqualityHelper("Bob", "Mary");
            /*
                Equals: 'Bob' does not equal 'Mary'
                Equals (ignore case): 'Bob' does not equal 'Mary'
                ==: 'Bob' does not equal 'Mary'
            */
            EqualityHelper(null, "");
            /*
                Equals: 'null' does not equal ''
                Equals (ignore case): 'null' does not equal ''
                ==: 'null' does not equal ''
            */
            EqualityHelper("", " ");
            /*
                Equals: '' does not equal ' '
                Equals (ignore case): '' does not equal ' '
                ==: '' does not equal ' '
            */
            EqualityHelper("Bob", "bob");
            /*
                Equals: 'Bob' does not equal 'bob'
                Equals (ignore case): 'Bob' equals 'bob'
                ==: 'Bob' does not equal 'bob'
            */

            public  static void EqualityHelper(string? testA, string? testB)
            {
                bool resultsBoolean;

                resultsBoolean = String.Equals(testA, testB);
                if (resultsBoolean)
                {
                    Console.WriteLine($"Equals: '{ testA ?? "null" }' equals '{ testB ?? "null" }'");
                }
                else
                {
                    Console.WriteLine($"Equals: '{ testA ?? "null" }' does not equal '{ testB ?? "null" }'");
                }

                resultsBoolean = String.Equals(testA, testB, StringComparison.InvariantCultureIgnoreCase);
                if (resultsBoolean)
                {
                    Console.WriteLine($"Equals (ignore case): '{ testA ?? "null" }' equals '{ testB ?? "null" }'");
                }
                else
                {
                    Console.WriteLine($"Equals (ignore case): '{ testA ?? "null" }' does not equal '{ testB ?? "null" }'");
                }

                resultsBoolean = testA == testB;
                if (resultsBoolean)
                {
                    Console.WriteLine($"==: '{ testA ?? "null" }' equals '{ testB ?? "null" }'");
                }
                else
                {
                    Console.WriteLine($"==: '{ testA ?? "null" }' does not equal '{ testB ?? "null" }'");
                }

                Console.WriteLine();
            }
        
```

## Getting a Substring
```c#

            string testString = "This is a test of substring. Let's see how its testing works out.";
            string results;

            results = testString.Substring(5);
            Console.WriteLine(results);
            //is a test of substring. Let's see how its testing works out.

            results = testString.Substring(5, 4);
            Console.WriteLine(results);
            //is a
        
```

## Replacing Text
```c#

            string testString = "This is a test of replace. Let's see how its testing Works out for test.";
            string results;

            results = testString.Replace("test", "trial");
            Console.WriteLine(results);
            //This is a trial of replace. Let's see how its trialing Works out for trial.

            results = testString.Replace(" test ", " trial ");
            Console.WriteLine(results);
            //This is a trial of replace. Let's see how its testing Works out for test.

            results = testString.Replace("works", "makes", StringComparison.InvariantCultureIgnoreCase);
            Console.WriteLine(results);
            //This is a test of replace. Let's see how its testing makes out for test.
        
```

## Inserting Text
```c#

            string testString = "This is a test of insert. Let's see how its testing Works out for test.";
            string results;

            results = testString.Insert(5, "(test) ");
            Console.WriteLine(results);
            //This (test) is a test of insert. Let's see how its testing Works out for test.
        
```

## Removing Text
```c#

            string testString = "This is a test of remove. Let's see how its testing Works out for test.";
            string results;

            results = testString.Remove(25);
            Console.WriteLine(results);
            //This is a test of remove.

            results = testString.Remove(14, 10);
            Console.WriteLine(results);
            //This is a test. Let's see how its testing Works out for test.
        
```