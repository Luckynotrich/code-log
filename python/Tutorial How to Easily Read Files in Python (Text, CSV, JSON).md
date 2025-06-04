## Read Files in Python

Files are everywhere: on computers, mobile devices, and across the cloud. Working with files is essential for every programmer, regardless of which programming language you're using.

File handling is a mechanism for creating a file, writing data, and reading data from it. The good news is that Python is enriched with packages for handling different file types.

In this tutorial, we'll learn how to handle files of different types. However, we'll focus more on [reading files with Python](http://https//app.dataquest.io/c/79/m/452/reading-and-writing-to-files/1/reading-files-in-python "reading files with Python").

After you finish this tutorial, you'll know how to do the following:

-   **Open files directly**
-   **Open files using the `with` context manager**
-   **Working with file modes in Python**
-   **Read text**
-   **Read CSV files**
-   **Read JSON files**

Let's dive in.

## Opening a File

Before accessing the contents of a file, we need to open the file. Python provides a built-in function that helps us open files in different modes. The `open()` function accepts two essential parameters: the file name and the mode; the default mode is `'r'`, which opens the file for reading only. The modes define how we can access a file and how we can manipulate its content. The `open()` function provides a few different modes that we'll discuss later in this tutorial.

First, let's try the function by opening a text file. Download the [text file](https://raw.githubusercontent.com/m-mehdi/tutorials/a78ef683f2716cfd431025768b3eedada45c9d47/zen_of_python.txt) containing the Zen of Python, and store it in the same path as your code.

```
f = open('zen_of_python.txt', 'r')
print(f.read())
f.close()
```

```
    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!
```

In the code above, the `open()` function opens the text file in the reading mode, allowing us to grab information from the file without accidentally changing it. In the first line, the output of the `open()` function is assigned to the `f` variable, an object representing the text file. In the second line of the code above, we use the `read()` method to read the entire file and print its content. The `close()` method closes the file in the last line. We must always close the opened files after we're done with them to release our computer resources and avoid raising exceptions.

### A Better Way to Read Files in Python

In Python, we can use the [`with` context manager](https://docs.python.org/3/reference/compound_stmts.html#with) to ensure a program releases the resources used after the file was closed, even if an exception has occurred. Let's try it:

```
with open('zen_of_python.txt') as f:
    print(f.read())
```

```
    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!
```

The code above creates a context using the `with` statement that the file object is no longer open out of the context. The bound variable, `f`, represents the file object that all the file object methods are accessible through the variable. The `read()` method reads the entire file in the second line, and then the `print()` function outputs the file content.

When the program reaches the end of the `with` statement block context, it closes the file to release the resources and ensures that other programs can use them. In general, using the `with` statement is a highly recommended practice when you're working with objects that need to be closed as soon as they're no longer required, such as files, databases, and network connections.

Notice that we have access to the `f` variable even after exiting the `with` context manager block; however, the file is closed. Let's try some of the file object properties to see if the variable is still alive and accessible:

```
print("Filename is '{}'.".format(f.name))
if f.closed:
    print("File is closed.")
else:
    print("File isn't closed.")
```

```
    Filename is 'zen_of_python.txt'.
    File is closed.
```

However, it's impossible to read from the file or write to the file. When a file is closed, any attempt to access its content leads to the following error:

```
f.read()
```

```
    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    ~\AppData\Local\Temp/ipykernel_9828/3059900045.py in <module>
    ----> 1 f.read()

    ValueError: I/O operation on closed file.
```

## Working with File Modes in Python

When you work with files in Python using the built-in `open()` function, you need to specify a mode. This tells Python exactly what you intend to do with the file – whether you want to read information from it, write new information, add to existing content, and more. It also determines if the file should be treated as plain text or as raw data (like an image). Here's a look at the main file modes:

| Mode | Description |
| --- | --- |
| `'r'` | Opens a file for **reading** (this is the default if you don't specify a mode). It will cause an error if the file doesn't exist. Python starts reading from the beginning of the file. |
| `'w'` | Opens a file for **writing**. If the file already exists, its entire content will be erased first. If the file doesn't exist, a new one will be created. |
| `'a'` | Opens a file for **appending**. New data will be added to the very end of the file. If the file doesn't exist, it will be created. Python will start writing at the end of the file. |
| `'x'` | Opens a file for **exclusive creation**. It will create a new file, but if a file with that name already exists, it will cause an error. |

Beyond these basic modes, you can also tell Python how to handle the file's content:

-   `'t'`: **Text mode** (this is the default). Python treats the file content as strings, automatically handling things like line endings and character encoding (usually using your system's default). So, just using `'r'` is the same as using `'rt'`.
-   `'b'`: **Binary mode**. Python treats the file content as raw bytes. This is essential for working with non-text files like images, audio files, or any data where you need precise control over the bytes.

You can also combine the primary modes (`'r'`, `'w'`, `'a'`, `'x'`) with `'+'` to enable both reading and writing:

-   `'r+'`: Opens a file for both reading and writing. The starting point for both is the beginning of the file, and it won't erase the existing content.
-   `'w+'`: Opens a file for both writing and reading. If the file exists, it will be emptied first. If it doesn't exist, a new one is created.
-   `'a+'`: Opens a file for both appending and reading. New writing will always happen at the end of the file, but you can move around and read from any point. If the file doesn't exist, it's created.
-   `'x+'`: Opens a file for exclusive creation, allowing both reading and writing. It will fail if the file already exists.

You can even combine the text/binary modes with these, for example, `'rb'` means reading in binary, and `'w+b'` means reading and writing in binary (and emptying the file first).

Let's look at copying an image file, [dataquest\_logo.png](https://raw.githubusercontent.com/m-mehdi/tutorials/8210bc95fdde6e46c393bd56298cee1a49ea08b1/dataquest_logo.png). Since images aren't text, we need to use binary mode:

```
source_image = 'dataquest_logo.png'
copied_image = 'data_quest_logo_copy.png'

with open(source_image, 'rb') as source_file:
  with open(copied_image, 'wb') as destination_file:
    for byte in source_file:
      destination_file.write(byte)
print(f"Successfully copied '{source_image}' to '{copied_image}'")
```

This code reads the original image file in binary mode (`'rb'`) and writes it byte by byte to a new file in binary mode (`'wb'`), creating an exact copy. We use a simple loop to go through each byte in the original and write it to the new file.

## Reading Text Files

Now that we have a good understanding of file modes, let's focus specifically on how to read the content of text files. The next part will cover some useful methods for doing just that.

So far, we've learned the entire content of a file can be read with the `read()` method. What if we only want to read a few bytes from a text file. To do that, specify the number of bytes in the `read()` method. Let's try it:

```
with open('zen_of_python.txt') as f:
    print(f.read(17))
```

```
The Zen of Python
```

The simple code above reads the first 17 bytes of the _zen\_of\_python.txt_ file and prints them out.

Sometimes, it makes more sense to read the content of a text file one line at a time. In this case, we can use the `readline()` method. Let's do it:

```
with open('zen_of_python.txt') as f:
    print(f.readline())
```

```
The Zen of Python, by Tim Peters
```

The code above returns the first line of the file. If we call the method one more time, it will return the second line in the file, etc., as follows:

```
with open('zen_of_python.txt') as f:
    print(f.readline())
    print(f.readline())
    print(f.readline())
    print(f.readline())
```

```
The Zen of Python, by Tim Peters  

Beautiful is better than ugly.

Explicit is better than implicit.
```

This useful method helps us to read the entire file incrementally. The following code outputs the entire file by iterating over it line by line until the file pointer that keeps track of where we're reading or writing the file reaches the end of the file. When the `readline()` method reaches the end of the file, it returns an empty string, `''`.with open('zen\_of\_python.txt') as f:

```
with open('zen_of_python.txt') as f:
    line = f.readline()
    while line:
        print(line, end='')
        line = f.readline()        
```

```
    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!
```

The code above reads the first line of the file outside the while loop and assigns it to the `line` variable. Inside the while loop, it prints the string stored in the `line` variable, then reads the next line of the file. The while loop iterates the process until the `readline()` method returns an empty string. The empty string evaluates to `False` in the while loop, so the iteration process terminates.

The other helpful method for reading text files is the `readlines()` method. Applying this method on a file object returns a list of strings containing each line of the file. Let's see how it works:

```
with open('zen_of_python.txt') as f:
    lines = f.readlines()
```

Let's check the data type of the `lines` variable and then print it:

```
print(type(lines))
print(lines)
```

```
<class 'list'>
['The Zen of Python, by Tim Peters\n', '\n', 'Beautiful is better than ugly.\n', 'Explicit is better than implicit.\n', 'Simple is better than complex.\n', 'Complex is better than complicated.\n', 'Flat is better than nested.\n', 'Sparse is better than dense.\n', 'Readability counts.\n', "Special cases aren't special enough to break the rules.\n", 'Although practicality beats purity.\n', 'Errors should never pass silently.\n', 'Unless explicitly silenced.\n', 'In the face of ambiguity, refuse the temptation to guess.\n', 'There should be one-- and preferably only one --obvious way to do it.\n', "Although that way may not be obvious at first unless you're Dutch.\n", 'Now is better than never.\n', 'Although never is often better than *right* now.\n', "If the implementation is hard to explain, it's a bad idea.\n", 'If the implementation is easy to explain, it may be a good idea.\n', "Namespaces are one honking great idea -- let's do more of those!"]
```

It's a list of strings wherein each item in the list is one line of the text file. The `\n` escape character represents a new line in the file. Also, we can access every item in the list by indexing or slicing operations:

```
print(lines)
print(lines[3:5])
print(lines[-1])
```

```
['The Zen of Python, by Tim Peters\n', '\n', 'Beautiful is better than ugly.\n', 'Explicit is better than implicit.\n', 'Simple is better than complex.\n', 'Complex is better than complicated.\n', 'Flat is better than nested.\n', 'Sparse is better than dense.\n', 'Readability counts.\n', "Special cases aren't special enough to break the rules.\n", 'Although practicality beats purity.\n', 'Errors should never pass silently.\n', 'Unless explicitly silenced.\n', 'In the face of ambiguity, refuse the temptation to guess.\n', 'There should be one-- and preferably only one --obvious way to do it.\n', "Although that way may not be obvious at first unless you're Dutch.\n", 'Now is better than never.\n', 'Although never is often better than *right* now.\n', "If the implementation is hard to explain, it's a bad idea.\n", 'If the implementation is easy to explain, it may be a good idea.\n', "Namespaces are one honking great idea -- let's do more of those!"]
['Explicit is better than implicit.\n', 'Simple is better than complex.\n']
Namespaces are one honking great idea -- let's do more of those!
```

## Reading CSV Files

So far, we've learned how to work with regular text files. However, sometimes data comes in a CSV format, and it's common for data professionals to retrieve required information and manipulate the content of CSV files.

We'll use the CSV module in this section. The CSV module provides helpful methods to read the comma-separated values stored in a CSV file. We'll try it right now, but first, you need to download the [`chocolate.csv`](https://raw.githubusercontent.com/m-mehdi/tutorials/main/chocolate.csv) file and store it in the current working directory:

```
import csv

with open('chocolate.csv') as f:
    reader = csv.reader(f, delimiter=',')
    for row in reader:
        print(row)
```

```
    ['Company', 'Bean Origin or Bar Name', 'REF', 'Review Date', 'Cocoa Percent', 'Company Location', 'Rating', 'Bean Type', 'Country of Origin']
    ['A. Morin', 'Agua Grande', '1876', '2016', '63%', 'France', '3.75', 'Â\xa0', 'Sao Tome']
    ['A. Morin', 'Kpime', '1676', '2015', '70%', 'France', '2.75', 'Â\xa0', 'Togo']
    ['A. Morin', 'Atsane', '1676', '2015', '70%', 'France', '3', 'Â\xa0', 'Togo']
    ['A. Morin', 'Akata', '1680', '2015', '70%', 'France', '3.5', 'Â\xa0', 'Togo']
    ['Acalli', 'Chulucanas, El Platanal', '1462', '2015', '70%', 'U.S.A.', '3.75', 'Â\xa0', 'Peru']
    ['Acalli', 'Tumbes, Norandino', '1470', '2015', '70%', 'U.S.A.', '3.75', 'Criollo', 'Peru']
    ['Adi', 'Vanua Levu', '705', '2011', '60%', 'Fiji', '2.75', 'Trinitario', 'Fiji']
    ['Adi', 'Vanua Levu, Toto-A', '705', '2011', '80%', 'Fiji', '3.25', 'Trinitario', 'Fiji']
    ['Adi', 'Vanua Levu', '705', '2011', '88%', 'Fiji', '3.5', 'Trinitario', 'Fiji']
    ['Adi', 'Vanua Levu, Ami-Ami-CA', '705', '2011', '72%', 'Fiji', '3.5', 'Trinitario', 'Fiji']
    ['Aequare (Gianduja)', 'Los Rios, Quevedo, Arriba', '370', '2009', '55%', 'Ecuador', '2.75', 'Forastero (Arriba)', 'Ecuador']
    ['Aequare (Gianduja)', 'Los Rios, Quevedo, Arriba', '370', '2009', '70%', 'Ecuador', '3', 'Forastero (Arriba)', 'Ecuador']
    ['Ah Cacao', 'Tabasco', '316', '2009', '70%', 'Mexico', '3', 'Criollo', 'Mexico']
    ["Akesson's (Pralus)", 'Bali (west), Sukrama Family, Melaya area', '636', '2011', '75%', 'Switzerland', '3.75', 'Trinitario', 'Indonesia']
    ["Akesson's (Pralus)", 'Madagascar, Ambolikapiky P.', '502', '2010', '75%', 'Switzerland', '2.75', 'Criollo', 'Madagascar']
    ["Akesson's (Pralus)", 'Monte Alegre, D. Badero', '508', '2010', '75%', 'Switzerland', '2.75', 'Forastero', 'Brazil']
    ['Alain Ducasse', 'Trinite', '1215', '2014', '65%', 'France', '2.75', 'Trinitario', 'Trinidad']
    ['Alain Ducasse', 'Vietnam', '1215', '2014', '75%', 'France', '2.75', 'Trinitario', 'Vietnam']
    ['Alain Ducasse', 'Madagascar', '1215', '2014', '75%', 'France', '3', 'Trinitario', 'Madagascar']
    ['Alain Ducasse', 'Chuao', '1061', '2013', '75%', 'France', '2.5', 'Trinitario', 'Venezuela']
    ['Alain Ducasse', 'Piura, Perou', '1173', '2013', '75%', 'France', '2.5', 'Â\xa0', 'Peru']
    ['Alexandre', 'Winak Coop, Napo', '1944', '2017', '70%', 'Netherlands', '3.5', 'Forastero (Nacional)', 'Ecuador']
    ['Alexandre', 'La Dalia, Matagalpa', '1944', '2017', '70%', 'Netherlands', '3.5', 'Criollo, Trinitario', 'Nicaragua']
    ['Alexandre', 'Tien Giang', '1944', '2017', '70%', 'Netherlands', '3.5', 'Trinitario', 'Vietnam']
    ['Alexandre', 'Makwale Village, Kyela', '1944', '2017', '70%', 'Netherlands', '3.5', 'Forastero', 'Tanzania']
    ['Altus aka Cao Artisan', 'Momotombo', '1728', '2016', '60%', 'U.S.A.', '2.75', 'Â\xa0', 'Nicaragua']
    ['Altus aka Cao Artisan', 'Bolivia', '1133', '2013', '60%', 'U.S.A.', '3', 'Â\xa0', 'Bolivia']
    ['Altus aka Cao Artisan', 'Peru', '1133', '2013', '60%', 'U.S.A.', '3.25', 'Â\xa0', 'Peru']
    ['Amano', 'Morobe', '725', '2011', '70%', 'U.S.A.', '4', 'Â\xa0', 'Papua New Guinea']
    ['Amano', 'Dos Rios', '470', '2010', '70%', 'U.S.A.', '3.75', 'Â\xa0', 'Dominican Republic']
    ['Amano', 'Guayas', '470', '2010', '70%', 'U.S.A.', '4', 'Â\xa0', 'Ecuador']
    ['Amano', 'Chuao', '544', '2010', '70%', 'U.S.A.', '3', 'Trinitario', 'Venezuela']
    ['Amano', 'Montanya', '363', '2009', '70%', 'U.S.A.', '3', 'Â\xa0', 'Venezuela']
    ['Amano', 'Bali, Jembrana', '304', '2008', '70%', 'U.S.A.', '2.75', 'Â\xa0', 'Indonesia']
    ['Amano', 'Madagascar', '129', '2007', '70%', 'U.S.A.', '3.5', 'Trinitario', 'Madagascar']
    ['Amano', 'Cuyagua', '147', '2007', '70%', 'U.S.A.', '3', 'Â\xa0', 'Venezuela']
    ['Amano', 'Ocumare', '175', '2007', '70%', 'U.S.A.', '3.75', 'Criollo', 'Venezuela']
    ['Amatller (Simon Coll)', 'Ghana', '322', '2009', '70%', 'Spain', '3', 'Forastero', 'Ghana']
    ['Amatller (Simon Coll)', 'Ecuador', '327', '2009', '70%', 'Spain', '2.75', 'Â\xa0', 'Ecuador']
    ['Amatller (Simon Coll)', 'Ecuador', '464', '2009', '85%', 'Spain', '2.75', 'Â\xa0', 'Ecuador']
    ['Amatller (Simon Coll)', 'Ghana', '464', '2009', '85%', 'Spain', '3', 'Forastero', 'Ghana']
    ['Amazona', 'LamasdelChanka, San Martin, Oro Verde coop', '1145', '2013', '72%', 'Peru', '3.25', 'Â\xa0', 'Peru']
    ['Ambrosia', 'Venezuela', '1498', '2015', '70%', 'Canada', '3.25', 'Â\xa0', 'Venezuela']
    ['Ambrosia', 'Peru', '1498', '2015', '68%', 'Canada', '3.5', 'Â\xa0', 'Peru']
    ['Amedei', 'Piura, Blanco de Criollo', '979', '2012', '70%', 'Italy', '3.75', 'Â\xa0', 'Peru']
    ['Amedei', 'Porcelana', '111', '2007', '70%', 'Italy', '4', 'Criollo (Porcelana)', 'Venezuela']
    ['Amedei', 'Nine', '111', '2007', '75%', 'Italy', '4', 'Blend', 'Â\xa0']
    ['Amedei', 'Chuao', '111', '2007', '70%', 'Italy', '5', 'Trinitario', 'Venezuela']
    ['Amedei', 'Ecuador', '123', '2007', '70%', 'Italy', '3', 'Trinitario', 'Ecuador']
    ['Amedei', 'Jamaica', '123', '2007', '70%', 'Italy', '3', 'Trinitario', 'Jamaica']
    ['Amedei', 'Grenada', '123', '2007', '70%', 'Italy', '3.5', 'Trinitario', 'Grenada']
    ['Amedei', 'Venezuela', '123', '2007', '70%', 'Italy', '3.75', 'Trinitario (85% Criollo)', 'Venezuela']
    ['Amedei', 'Madagascar', '123', '2007', '70%', 'Italy', '4', 'Trinitario (85% Criollo)', 'Madagascar']
    ['Amedei', 'Trinidad', '129', '2007', '70%', 'Italy', '3.5', 'Trinitario', 'Trinidad']
    ['Amedei', 'Toscano Black', '170', '2007', '63%', 'Italy', '3.5', 'Blend', 'Â\xa0']
    ['Amedei', 'Toscano Black', '40', '2006', '70%', 'Italy', '5', 'Blend', 'Â\xa0']
    ['Amedei', 'Toscano Black', '75', '2006', '66%', 'Italy', '4', 'Blend', 'Â\xa0']
    ['AMMA', 'Catongo', '1065', '2013', '75%', 'Brazil', '3.25', 'Forastero (Catongo)', 'Brazil']
    ['AMMA', 'Monte Alegre, 3 diff. plantations', '572', '2010', '85%', 'Brazil', '2.75', 'Forastero (Parazinho)', 'Brazil']
    ['AMMA', 'Monte Alegre, 3 diff. plantations', '572', '2010', '50%', 'Brazil', '3.75', 'Forastero (Parazinho)', 'Brazil']
    ['AMMA', 'Monte Alegre, 3 diff. plantations', '572', '2010', '75%', 'Brazil', '3.75', 'Forastero (Parazinho)', 'Brazil']
    ['AMMA', 'Monte Alegre, 3 diff. plantations', '572', '2010', '60%', 'Brazil', '4', 'Forastero (Parazinho)', 'Brazil']
    ['Anahata', 'Elvesia', '1259', '2014', '75%', 'U.S.A.', '3', 'Â\xa0', 'Dominican Republic']
    ['Animas', 'Alto Beni', '1852', '2016', '75%', 'U.S.A.', '3.5', 'Â\xa0', 'Bolivia']
    ['Ara', 'Madagascar', '1375', '2014', '75%', 'France', '3', 'Trinitario', 'Madagascar']
    ['Ara', 'Chiapas', '1379', '2014', '72%', 'France', '2.5', 'Â\xa0', 'Mexico']
    ['Arete', 'Camino Verde', '1602', '2015', '75%', 'U.S.A.', '3.5', 'Â\xa0', 'Ecuador']
    ['Artisan du Chocolat', 'Congo', '300', '2008', '72%', 'U.K.', '3.75', 'Forastero', 'Congo']
    ['Artisan du Chocolat (Casa Luker)', 'Orinoqua Region, Arauca', '1181', '2013', '72%', 'U.K.', '2.75', 'Trinitario', 'Colombia']
    ['Askinosie', 'Mababa', '1780', '2016', '68%', 'U.S.A.', '3.75', 'Trinitario', 'Tanzania']
    ['Askinosie', 'Tenende, Uwate', '647', '2011', '72%', 'U.S.A.', '3.75', 'Trinitario', 'Tanzania']
    ['Askinosie', 'Cortes', '661', '2011', '70%', 'U.S.A.', '3.75', 'Trinitario', 'Honduras']
    ['Askinosie', 'Davao', '331', '2009', '77%', 'U.S.A.', '3.75', 'Trinitario', 'Philippines']
    ['Askinosie', 'Xoconusco', '141', '2007', '75%', 'U.S.A.', '2.5', 'Trinitario', 'Mexico']
    ['Askinosie', 'San Jose del Tambo', '175', '2007', '70%', 'U.S.A.', '3', 'Forastero (Arriba)', 'Ecuador']
    ['Bahen & Co.', 'Houseblend', '999', '2012', '70%', 'Australia', '2.5', 'Blend', 'Â\xa0']
    ['Bakau', 'Bambamarca, 2015', '1454', '2015', '70%', 'Peru', '2.75', 'Â\xa0', 'Peru']
    ['Bakau', 'Huallabamba, 2015', '1454', '2015', '70%', 'Peru', '3.5', 'Â\xa0', 'Peru']
    ['Bar Au Chocolat', 'Bahia', '1554', '2015', '70%', 'U.S.A.', '3.5', 'Â\xa0', 'Brazil']
    ['Bar Au Chocolat', 'Maranon Canyon', '1295', '2014', '70%', 'U.S.A.', '4', 'Forastero (Nacional)', 'Peru']
    ['Bar Au Chocolat', 'Duarte Province', '983', '2012', '70%', 'U.S.A.', '3.25', 'Â\xa0', 'Dominican Republic']
    ['Bar Au Chocolat', 'Chiapas', '983', '2012', '70%', 'U.S.A.', '3.5', 'Â\xa0', 'Mexico']
    ['Bar Au Chocolat', 'Sambirano', '983', '2012', '70%', 'U.S.A.', '3.75', 'Trinitario', 'Madagascar']
    ["Baravelli's", 'single estate', '955', '2012', '80%', 'Wales', '2.75', 'Â\xa0', 'Costa Rica']
    ['Batch', 'Dominican Republic, Batch 3', '1840', '2016', '65%', 'U.S.A.', '3.5', 'Â\xa0', 'Domincan Republic']
    ['Batch', 'Brazil', '1868', '2016', '70%', 'U.S.A.', '3.75', 'Â\xa0', 'Brazil']
    ['Batch', 'Ecuador', '1880', '2016', '65%', 'U.S.A.', '3.25', 'Â\xa0', 'Ecuador']
    ['Beau Cacao', 'Asajaya E, NW Borneo, b. #132/4500', '1948', '2017', '73%', 'U.K.', '3', 'Â\xa0', 'Malaysia']
    ['Beau Cacao', 'Serian E., NW Borneo, b. #134/3800', '1948', '2017', '72%', 'U.K.', '3.25', 'Â\xa0', 'Malaysia']
    ['Beehive', 'Brazil, Batch 20316', '1784', '2016', '80%', 'U.S.A.', '2.75', 'Â\xa0', 'Brazil']
    ['Beehive', 'Dominican Republic, Batch 31616', '1784', '2016', '70%', 'U.S.A.', '2.75', 'Â\xa0', 'Domincan Republic']
    ['Beehive', 'Ecuador, Batch 31516', '1784', '2016', '70%', 'U.S.A.', '2.75', 'Â\xa0', 'Ecuador']
    ['Beehive', 'Ecuador', '1788', '2016', '90%', 'U.S.A.', '2.75', 'Â\xa0', 'Ecuador']
    ['Belcolade', 'Costa Rica', '586', '2010', '64%', 'Belgium', '2.75', 'Â\xa0', 'Costa Rica']
    ['Belcolade', 'Papua New Guinea', '586', '2010', '64
    ['Belcolade', 'Peru', '586', '2010', '64%', 'Belgium', '2.75', 'Â\xa0', 'Peru']
    ['Belcolade', 'Ecuador', '586', '2010', '71%', 'Belgium', '3.5', 'Â\xa0', 'Ecuador']
    ['Bellflower', 'Kakao Kamili, Kilombero Valley', '1800', '2016', '70%', 'U.S.A.', '3.5', 'Criollo, Trinitario', 'Tanzania']
    ['Bellflower', 'Alto Beni, Palos Blanco', '1804', '2016', '70%', 'U.S.A.', '3.25', 'Â\xa0', 'Bolivia']
    ['Vintage Plantations (Tulicorp)', 'Los Rios, Rancho Grande 2007', '153', '2007', '65%', 'U.S.A.', '3', 'Forastero (Arriba)', 'Ecuador']
    ['Violet Sky', 'Sambirano Valley', '1458', '2015', '77%', 'U.S.A.', '2.75', 'Trinitario', 'Madagascar']
    ['Wm', 'Wild Beniano, 2016, batch 128, Heirloom', '1912', '2016', '76%', 'U.S.A.', '3.5', 'Â\xa0', 'Bolivia']
    ['Wm', 'Ghana, 2013, batch 129', '1916', '2016', '75%', 'U.S.A.', '3.75', 'Â\xa0', 'Ghana']
    ['Woodblock', 'La Red', '769', '2011', '70%', 'U.S.A.', '3.5', 'Â\xa0', 'Dominican Republic']
    ['Xocolat', 'Hispaniola', '1057', '2013', '66%', 'Domincan Republic', '3', 'Â\xa0', 'Dominican Republic']
    ['Xocolla', 'Sambirano, batch 170102', '1948', '2017', '70%', 'U.S.A.', '2.75', 'Â\xa0', 'Madagascar']
    ['Xocolla', 'Hispaniola, batch 170104', '1948', '2017', '70%', 'U.S.A.', '2.5', 'Â\xa0', 'Dominican Republic']
    ['Zart Pralinen', 'UNOCACE', '1824', '2016', '70%', 'Austria', '2.75', 'Nacional (Arriba)', 'Ecuador']
    ['Zart Pralinen', 'San Juan Estate', '1824', '2016', '85%', 'Austria', '2.75', 'Trinitario', 'Trinidad']
    ['Zokoko', 'Guadalcanal', '1716', '2016', '78%', 'Australia', '3.75', 'Â\xa0', 'Solomon Islands']
```

Each row of the CSV file forms a list wherein every item can be easily accessed, as follows:

```
import csv

with open('chocolate.csv') as f:
    reader = csv.reader(f, delimiter=',')
    for row in reader:
        print("The {} company is located in {}.".format(row[0], row[5]))
```

```
    The Company company is located in Company Location.
    The A. Morin company is located in France.
    The A. Morin company is located in France.
    The A. Morin company is located in France.
    The A. Morin company is located in France.
    The Acalli company is located in U.S.A..
    The Acalli company is located in U.S.A..
    The Adi company is located in Fiji.
    The Adi company is located in Fiji.
    The Adi company is located in Fiji.
    The Adi company is located in Fiji.
    The Aequare (Gianduja) company is located in Ecuador.
    The Aequare (Gianduja) company is located in Ecuador.
    The Ah Cacao company is located in Mexico.
    The Akesson's (Pralus) company is located in Switzerland.
    The Akesson's (Pralus) company is located in Switzerland.
    The Akesson's (Pralus) company is located in Switzerland.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alexandre company is located in Netherlands.
    The Alexandre company is located in Netherlands.
    The Alexandre company is located in Netherlands.
    The Alexandre company is located in Netherlands.
    The Altus aka Cao Artisan company is located in U.S.A..
    The Altus aka Cao Artisan company is located in U.S.A..
    The Altus aka Cao Artisan company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amatller (Simon Coll) company is located in Spain.
    The Amatller (Simon Coll) company is located in Spain.
    The Amatller (Simon Coll) company is located in Spain.
    The Amatller (Simon Coll) company is located in Spain.
    The Amazona company is located in Peru.
    The Ambrosia company is located in Canada.
    The Ambrosia company is located in Canada.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The Anahata company is located in U.S.A..
    The Animas company is located in U.S.A..
    The Ara company is located in France.
    The Ara company is located in France.
    The Arete company is located in U.S.A..
    The Artisan du Chocolat company is located in U.K..
    The Artisan du Chocolat (Casa Luker) company is located in U.K..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Bahen & Co. company is located in Australia.
    The Bakau company is located in Peru.
    The Bakau company is located in Peru.
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Baravelli's company is located in Wales.
    The Batch company is located in U.S.A..
    The Batch company is located in U.S.A..
    The Batch company is located in U.S.A..
    The Beau Cacao company is located in U.K..
    The Beau Cacao company is located in U.K..
    The Beehive company is located in U.S.A..
    The Beehive company is located in U.S.A..
    The Beehive company is located in U.S.A..
    The Beehive company is located in U.S.A..
    The Belcolade company is located in Belgium.
    The Belcolade company is located in Belgium.
    The Belcolade company is located in Belgium.
    The Belcolade company is located in Belgium.
    The Bellflower company is located in U.S.A..
    The Bellflower company is located in U.S.A..
    The Vintage Plantations (Tulicorp) company is located in U.S.A..
    The Violet Sky company is located in U.S.A..
    The Wm company is located in U.S.A..
    The Wm company is located in U.S.A..
    The Woodblock company is located in U.S.A..
    The Xocolat company is located in Domincan Republic.
    The Xocolla company is located in U.S.A..
    The Xocolla company is located in U.S.A..
    The Zart Pralinen company is located in Austria.
    The Zart Pralinen company is located in Austria.
    The Zokoko company is located in Australia.
```

It's possible to use the name of the columns instead of using their indices, which is usually more convenient for developers. In this case, instead of using the `reader()` method, we use the `DictReader()` method that returns a collection of dictionary objects. Let's try it:

```
import csv

with open('chocolate.csv') as f:
    dict_reader = csv.DictReader(f, delimiter=',')
    for row in dict_reader:
        print("The {} company is located in {}.".format(row['Company'], row['Company Location']))
```

```
    The A. Morin company is located in France.
    The A. Morin company is located in France.
    The A. Morin company is located in France.
    The A. Morin company is located in France.
    The Acalli company is located in U.S.A..
    The Acalli company is located in U.S.A..
    The Adi company is located in Fiji.
    The Adi company is located in Fiji.
    The Adi company is located in Fiji.
    The Adi company is located in Fiji.
    The Aequare (Gianduja) company is located in Ecuador.
    The Aequare (Gianduja) company is located in Ecuador.
    The Ah Cacao company is located in Mexico.
    The Akesson's (Pralus) company is located in Switzerland.
    The Akesson's (Pralus) company is located in Switzerland.
    The Akesson's (Pralus) company is located in Switzerland.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alain Ducasse company is located in France.
    The Alexandre company is located in Netherlands.
    The Alexandre company is located in Netherlands.
    The Alexandre company is located in Netherlands.
    The Alexandre company is located in Netherlands.
    The Altus aka Cao Artisan company is located in U.S.A..
    The Altus aka Cao Artisan company is located in U.S.A..
    The Altus aka Cao Artisan company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amano company is located in U.S.A..
    The Amatller (Simon Coll) company is located in Spain.
    The Amatller (Simon Coll) company is located in Spain.
    The Amatller (Simon Coll) company is located in Spain.
    The Amatller (Simon Coll) company is located in Spain.
    The Amazona company is located in Peru.
    The Ambrosia company is located in Canada.
    The Ambrosia company is located in Canada.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The Amedei company is located in Italy.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The AMMA company is located in Brazil.
    The Anahata company is located in U.S.A..
    The Animas company is located in U.S.A..
    The Ara company is located in France.
    The Ara company is located in France.
    The Arete company is located in U.S.A..
    The Artisan du Chocolat company is located in U.K..
    The Artisan du Chocolat (Casa Luker) company is located in U.K..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Askinosie company is located in U.S.A..
    The Bahen & Co. company is located in Australia.
    The Bakau company is located in Peru.
    The Bakau company is located in Peru.
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Bar Au Chocolat company is located in U.S.A..
    The Baravelli's company is located in Wales.
    The Batch company is located in U.S.A..
    The Batch company is located in U.S.A..
    The Batch company is located in U.S.A..
    The Beau Cacao company is located in U.K..
    The Beau Cacao company is located in U.K..
    The Beehive company is located in U.S.A..
    The Beehive company is located in U.S.A..
    The Beehive company is located in U.S.A..
    The Beehive company is located in U.S.A..
    The Belcolade company is located in Belgium.
    The Belcolade company is located in Belgium.
    The Belcolade company is located in Belgium.
    The Belcolade company is located in Belgium.
    The Bellflower company is located in U.S.A..
    The Bellflower company is located in U.S.A..
    The Vintage Plantations (Tulicorp) company is located in U.S.A..
    The Violet Sky company is located in U.S.A..
    The Wm company is located in U.S.A..
    The Wm company is located in U.S.A..
    The Woodblock company is located in U.S.A..
    The Xocolat company is located in Domincan Republic.
    The Xocolla company is located in U.S.A..
    The Xocolla company is located in U.S.A..
    The Zart Pralinen company is located in Austria.
    The Zart Pralinen company is located in Austria.
    The Zokoko company is located in Australia.
```

## Reading JSON Files

Another popular file format that we mainly use for storing and exchanging data is JSON. JSON stands for JavaScript Object Notation, and it allows us to store data with key-value pairs separated by commas.

In this section, we're going to load a JSON file and work with it as a JSON object — not as a text file. To do that, we need to import the JSON module. Then, in the `with` context manager, we use the `load()` method that belongs to the `json` object. It loads the file's content and stores it in the `context` variable as a dictionary. Let's try it, but before running the code, download the [`movie.json`](https://raw.githubusercontent.com/m-mehdi/tutorials/main/movie.json) file and put it in the current working directory.

```
import json
with open('movie.json') as f:
    content = json.load(f)
    print(content)
```

```
    {'Title': 'Bicentennial Man', 'Release Date': 'Dec 17 1999', 'MPAA Rating': 'PG', 'Running Time min': 132, 'Distributor': 'Walt Disney Pictures', 'Source': 'Based on Book/Short Story', 'Major Genre': 'Drama', 'Creative Type': 'Science Fiction', 'Director': 'Chris Columbus', 'Rotten Tomatoes Rating': 38, 'IMDB Rating': 6.4, 'IMDB Votes': 28827}
```

Let's check the data type of the `content` variable:

```
print(type(content))
```

```
    <class 'dict'>
```

Its data type is a dictionary. So we can access each piece of information stored in the JSON file with its key. Let's see how we can retrieve data from it:

```
print('{} directed by {}'.format(content['Title'], content['Director']))
```

```
    Bicentennial Man directed by Chris Columbus
```

## Wrapping Up

This tutorial discussed file handling in Python, focusing on reading the content of files. You learned about the `open()` built-in function, the with context manager, and how to read the common file types such as text, CSV, and JSON.