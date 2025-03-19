```python
%load_ext autoreload
%autoreload 2
```

    The autoreload extension is already loaded. To reload it, use:
      %reload_ext autoreload


# Functions vs. Methods

Sometimes people do not realize there is a difference between functions and methods. It is important to be able to know the difference and when and how to call them. In your coding journey you will likely encounter functions, methods, and class methods. Understanding the difference will allow you to utilize these tools to their greatest effect.

## Functions
Lets start with functions since everyone that has written any code has used one wether or not they have recognized it.

### What is a function?
- A function is a coding operation that performs a task when called, independent of a class.
- example: pd.read_csv() -- calling this pandas function reads in a file from the path provided.
- to call a pandas function, you first need to import with `import pandas as pd`, since pandas is not default within python.
<br><br>
- *note: Without getting into too much detail, even using `+` or other operators is calling a function.*


```python
# example of importing pandas and calling a function from it
import pandas as pd

pd.read_csv("../data/dc-comics.csv")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>page_id</th>
      <th>name</th>
      <th>urlslug</th>
      <th>ID</th>
      <th>ALIGN</th>
      <th>EYE</th>
      <th>HAIR</th>
      <th>SEX</th>
      <th>ALIVE</th>
      <th>APPEARANCES</th>
      <th>FIRST APPEARANCE</th>
      <th>YEAR</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1422</td>
      <td>Batman (Bruce Wayne)</td>
      <td>\/wiki\/Batman_(Bruce_Wayne)</td>
      <td>Secret Identity</td>
      <td>Good Characters</td>
      <td>Blue Eyes</td>
      <td>Black Hair</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>3093.0</td>
      <td>1939, May</td>
      <td>1939.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>23387</td>
      <td>Superman (Clark Kent)</td>
      <td>\/wiki\/Superman_(Clark_Kent)</td>
      <td>Secret Identity</td>
      <td>Good Characters</td>
      <td>Blue Eyes</td>
      <td>Black Hair</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>2496.0</td>
      <td>1986, October</td>
      <td>1986.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1458</td>
      <td>Green Lantern (Hal Jordan)</td>
      <td>\/wiki\/Green_Lantern_(Hal_Jordan)</td>
      <td>Secret Identity</td>
      <td>Good Characters</td>
      <td>Brown Eyes</td>
      <td>Brown Hair</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>1565.0</td>
      <td>1959, October</td>
      <td>1959.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1659</td>
      <td>James Gordon (New Earth)</td>
      <td>\/wiki\/James_Gordon_(New_Earth)</td>
      <td>Public Identity</td>
      <td>Good Characters</td>
      <td>Brown Eyes</td>
      <td>White Hair</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>1316.0</td>
      <td>1987, February</td>
      <td>1987.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1576</td>
      <td>Richard Grayson (New Earth)</td>
      <td>\/wiki\/Richard_Grayson_(New_Earth)</td>
      <td>Secret Identity</td>
      <td>Good Characters</td>
      <td>Blue Eyes</td>
      <td>Black Hair</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>1237.0</td>
      <td>1940, April</td>
      <td>1940.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>6891</th>
      <td>66302</td>
      <td>Nadine West (New Earth)</td>
      <td>\/wiki\/Nadine_West_(New_Earth)</td>
      <td>Public Identity</td>
      <td>Good Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Female Characters</td>
      <td>Living Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6892</th>
      <td>283475</td>
      <td>Warren Harding (New Earth)</td>
      <td>\/wiki\/Warren_Harding_(New_Earth)</td>
      <td>Public Identity</td>
      <td>Good Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6893</th>
      <td>283478</td>
      <td>William Harrison (New Earth)</td>
      <td>\/wiki\/William_Harrison_(New_Earth)</td>
      <td>Public Identity</td>
      <td>Good Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6894</th>
      <td>283471</td>
      <td>William McKinley (New Earth)</td>
      <td>\/wiki\/William_McKinley_(New_Earth)</td>
      <td>Public Identity</td>
      <td>Good Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6895</th>
      <td>150660</td>
      <td>Mookie (New Earth)</td>
      <td>\/wiki\/Mookie_(New_Earth)</td>
      <td>Public Identity</td>
      <td>Bad Characters</td>
      <td>Blue Eyes</td>
      <td>Blond Hair</td>
      <td>Male Characters</td>
      <td>Living Characters</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>6896 rows × 12 columns</p>
</div>



## Methods

### What is a method?
- A method is a function of a class object that operates on the objects data.
- i.e. all methods are functions but not all functions are methods.
- Methods are functions that you will typically always need when using the class. 
- calling structure: class_object.method() 
- Again to call a method or use the class, you need to import your class.
- For this tutorial I will be using the class `DNASeq`.



```python
from dnaseq import DNASeq  # Importing the DNASeq class from the dnaseq module

# Example usage of the DNASeq class
dna_sequence = DNASeq("ATCGTAGCTAGCTAGCTAGCTAGCTAGCTAGC")
print(f"Original sequence: {dna_sequence.sequence}")  # Prints the DNA sequence

# Example reverse_compliment method call
print(
    f"Reverse compliment sequence: {dna_sequence.reverse_complement()}"
)  # Prints the reverse complement of the DNA sequence
```

    Original sequence: ATCGTAGCTAGCTAGCTAGCTAGCTAGCTAGC
    Reverse compliment sequence: GCTAGCTAGCTAGCTAGCTAGCTAGCTACGAT


## Class Methods

### What is a class method?
- A class method is a function in a class that can be called outside of the class.
- These are useful in unique scenarios, such as an alternate way to create an object, that are useful when working with a class. 
- calling structure: Class.class_method(arg)


```python
# remember I have already imported DNASeq above

# Example useage of from_rna class method
rna_sequence = DNASeq.from_rna("AUGCUAGCUAGCUAGCUAGCUAGCUAGCUAGC")
print(
    f"RNA sequence converted to DNA: {rna_sequence.sequence}"
)  # Prints the DNA sequence converted from RNA
```

    RNA sequence converted to DNA: ATGCTAGCTAGCTAGCTAGCTAGCTAGCTAGC


# Summary
Functions perform a computational task when called. Methods and class methods are more specialized functions associated with a class and are called differently. Remember, all methods are functions but not all functions are methods. 

## When to use functions
- when you need to perform an operation that is independent of a specific data type.
- general utility operations that work across different contexts.
- example: reading in a csv file.

## When to use methods
- When you want to perform a specific function on an object's data.
- When the function operation is directly applicable to the class.
- reverse_complement()

## When to use class methods
- When you need an additional way to create an object.
- When you need to perform operations related to the class itself rather than specific instances.
- example: reading RNA rather than DNA.
