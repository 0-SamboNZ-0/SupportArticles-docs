---
title: Compute/compare hash values by using C#
description: Describes how to obtain a hash value and how to compare two hash values to check whether they are identical by using Visual C#. This article also provides a code sample to show how to perform this task.
ms.date: 04/13/2020
ms.prod-support-area-path: 
ms.reviewer: v-ingor
ms.topic: how-to
---
# Use Visual C# to compute and compare hash values

This article describes how to obtain a hash value and how to compare two hash values to check whether they are identical by using Visual C#.

_Original product version:_ &nbsp; Visual C#  
_Original KB number:_ &nbsp; 307020

## Summary

This step-by-step article shows you how to obtain a hash value and how to compare two hash values to check whether they are identical. This article also provides a code sample to show how to perform this task.

This article refers to the following Microsoft .NET Framework Class Library namespaces:

- `System.Security.Cryptography`
- `System.Text`

The `System.Security.Cryptography` class in the .NET Framework makes it easy to compute a hash value for your source data.

## Compute a hash value

It is easy to generate and compare hash values using the cryptographic resources contained in the `System.Security.Cryptography` namespace. Because all hash functions take input of type `Byte[]`, it might be necessary to convert the source into a byte array before it is hashed. To create a hash for a string value, follow these steps:

1. Open Visual Studio .NET or Visual Studio.
2. Create a new Console Application in Visual C# .NET or in Visual C#  creates a public class for you along with an empty `Main()` method.

    > [!NOTE]
    > In Visual C#. NET, *Class1.cs* is created by default. In Visual C#, *Program.cs* is created by default.

3. Use the `using` directive on the `System`, `System.Security.Cryptography` and `System.Text` namespaces so that you are not required to qualify declarations from these namespaces later in your code. These statements must be used prior to any other declarations.

    ```csharp
    using System;
    using System.Security.Cryptography;
    using System.Text;
    ```

4. Declare a string variable to hold your source data, and two byte arrays (of undefined size) to hold the source bytes and the resulting hash value.

    ```csharp
    string sSourceData;
    byte[] tmpSource;
    byte[] tmpHash;
    ```

5. Use the `GetBytes()` method, which is a member of the `System.Text.ASCIIEncoding` class, to convert your source string into an array of bytes (required as input to the hashing function).

    ```csharp
    sSourceData = "MySourceData";
    //Create a byte array from source data.
    tmpSource = ASCIIEncoding.ASCII.GetBytes(sSourceData);
    ```

6. Compute the MD5 hash for your source data by calling `ComputeHash` on an instance of the `MD5CryptoServiceProvider` class.

    > [!NOTE]
    > To compute another hash value, you will need to create another instance of the class.

    ```csharp
    //Compute hash based on source data.
    tmpHash = new MD5CryptoServiceProvider().ComputeHash(tmpSource);
    ```

7. The `tmpHash` byte array now holds the computed hash value (128-bit value=16 bytes) for your source data. It is often useful to display or store a value like this as a hexadecimal string, which the following code accomplishes:

    ```csharp
    Console.WriteLine(ByteArrayToString(tmpHash));
    static string ByteArrayToString(byte[] arrInput)
    {
        int i;
        StringBuilder sOutput = new StringBuilder(arrInput.Length);
        for (i=0;i < arrInput.Length; i++)
        {
            sOutput.Append(arrInput[i].ToString("X2"));
        }
        return sOutput.ToString();
    }
    ```

8. Save and then run your code to see the resulting hexadecimal string for the source value.

## Compare two hash values

One of the purposes of creating a hash from source data is to provide a way to see if data has changed over time, or to compare two values without ever working with the actual values. In either case, you need to compare two computed hashes, which is easy if they are both stored as hexadecimal strings (as in the last step of the above section). However, it is quite possible that they will both be in the form of byte arrays. The following code, which continues from the code created in the previous section, shows how to compare two byte arrays.

1. Just below the creation of a hexadecimal string, create a new hash value based on new source data.

    ```csharp
    sSourceData = "NotMySourceData";
    tmpSource = ASCIIEncoding.ASCII.GetBytes(sSourceData);
    byte[] tmpNewHash;
    tmpNewHash = new MD5CryptoServiceProvider().ComputeHash(tmpSource);
    ```

2. The most straightforward way to compare two byte arrays is to loop through the arrays, comparing each individual element to its counterpart from the second value. If any elements are different, or if the two arrays are not the same size, the two values are not equal.

    ```csharp
    bool bEqual = false;
    if (tmpNewHash.Length == tmpHash.Length)
    {
        int i=0;
        while ((i < tmpNewHash.Length) && (tmpNewHash[i] == tmpHash[i]))
        {
            i += 1;
        }
        if (i == tmpNewHash.Length)
        {
            bEqual = true;
        }
    }

    if (bEqual)
        Console.WriteLine("The two hash values are the same");
    else
        Console.WriteLine("The two hash values are not the same");
    Console.ReadLine();
    ```

3. Save and then run your project to view the hexadecimal string created from the first hash value, and to find out if the new hash is equal to the original.

## Complete code listing

```csharp
using System;
using System.Security.Cryptography;
using System.Text;

namespace ComputeAHash_csharp
{
    /// <summary>
    /// Summary description for Class1.
    /// </summary>
    class Class1
    {
        static void Main(string[] args)
        {
            string sSourceData;
            byte[] tmpSource;
            byte[] tmpHash;
            sSourceData = "MySourceData";
            //Create a byte array from source data
            tmpSource = ASCIIEncoding.ASCII.GetBytes(sSourceData);

            //Compute hash based on source data
            tmpHash = new MD5CryptoServiceProvider().ComputeHash(tmpSource);
            Console.WriteLine(ByteArrayToString(tmpHash));

            sSourceData = "NotMySourceData";
            tmpSource = ASCIIEncoding.ASCII.GetBytes(sSourceData);

            byte[] tmpNewHash;

            tmpNewHash = new MD5CryptoServiceProvider().ComputeHash(tmpSource);

            bool bEqual = false;
            if (tmpNewHash.Length == tmpHash.Length)
            {
                int i=0;
                while ((i < tmpNewHash.Length) && (tmpNewHash[i] == tmpHash[i]))
                {
                    i += 1;
                }
                if (i == tmpNewHash.Length)
                {
                    bEqual = true;
                }
            }

            if (bEqual)
                Console.WriteLine("The two hash values are the same");
            else
                Console.WriteLine("The two hash values are not the same");
            Console.ReadLine();
        }

        static string ByteArrayToString(byte[] arrInput)
        {
            int i;
            StringBuilder sOutput = new StringBuilder(arrInput.Length);
            for (i=0;i < arrInput.Length -1; i++)
            {
                sOutput.Append(arrInput[i].ToString("X2"));
            }
            return sOutput.ToString();
        }
    }
}
```

## References

For more information about how to use the cryptographic features of the .NET Framework, see [.NET](https://dotnet.microsoft.com/).
