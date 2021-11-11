
## Table of Contents

- [Nomenclature](#nomenclature)
    + [Packages](#packages)
    + [Classes & Interfaces](#classes--interfaces)
    + [Methods](#methods)
    + [Fields](#fields)
    + [Variables & Parameters](#variables--parameters)
    + [Misc](#misc)
- [Declarations](#declarations)
    + [Visibility Modifiers](#visibility-modifiers)
    + [Access Level Modifiers](#access-level-modifiers)  
    + [Fields & Variables](#fields--variables)  
    + [Classes](#classes)
    + [Data Type Objects](#data-type-objects)
    + [Enum Classes](#enum-classes)
- [Spacing](#spacing)
    + [Indentation](#indentation)
    + [Line Length](#line-length)
    + [Vertical Spacing](#vertical-spacing)
- [Comments](#comments)
- [Getters & Setters](#getters--setters)
- [Brace Style](#brace-style)
- [Conditional Statements](#conditional-statements)
- [Switch Statements](#switch-statements)
- [XML Guidance](#xml-guidance)
  + [XML File Names](#xml-file-names)
  + [XML Indentation](#xml-indentation)
  + [Use Context-Specific XML Files](#use-context-specific-xml-files)
  + [XML Attribute Ordering](#xml-attribute-ordering)
- [Language](#language)


## Nomenclature

On the whole, naming should follow Java standards.

### Packages

Package names are similar to Java: all __lower-case__, multiple words concatenated together, without hypens or underscores:

__BAD__:

```java
package com.PackageName.some_name;
```

__GOOD__:

```java
package com.packagename.somename;
```

### Classes & Interfaces

Written in __UpperCamelCase__. For example `RadialSlider`.

### Methods

Written in __lowerCamelCase__. For example `setValue`.

### Fields

Generally, written in __lowerCamelCase__.

Example field names:

```java
class MyClass {
  int publicField = 0;
  public Person person = new Person();
  private int privateField;
}
```

Constant values in the companion object should be written in __uppercase__, with an underscore separating words:

```java
class MyClass {
  private final int THE_ANSWER = 42;
}
```

### Variables & Parameters

Written in __lowerCamelCase__.

Single character values must be avoided, for temporary looping variables it may be used.

Example:

__GOOD__:
```java
for (String item : collection) {
    println(item);
}
for (int i = 0; i<10; i++ ) {
    println(times);
}
```

__BAD__:
```java
for (String i : collection) {
    println(i);
}
for (int item = 0; item<10; item++ ) {
    println(item);
}
```
### Misc

In code, acronyms should be treated as words. For example:

__BAD:__

```
XMLHTTPRequest
URL: String? 
findPostByID
```
__GOOD:__

```
XmlHttpRequest
url: String
findPostById
```

## Declarations

### Visibility Modifiers

Only include visibility modifiers if you need something other than the default of protected.

**GOOD:**

```java
public int wideOpenProperty = 1;
private String myOwnPrivateProperty = "private";
double myProtectedProperty = 18.2;
```

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.

### Fields & Variables

Prefer single declaration per line.

### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.

### Data Type Objects

Prefer classes for simple data holding objects.

__Example:__

```java
public class Person {
  public String name;
  public int age;

  public Person(String name, int age) {
    this.name = name;
    this.age = age;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public int getAge() {
    return age;
  }

  public void setAge(int age) {
    this.age = age;
  }
}
```

### Enum Classes

Enum classes without methods may be formatted without line-breaks, as follows:

```java
public enum location {NORTH,EAST,SOUTH,WEST}
```

Enum classes may also be formatted with line-breaks, as follows:
```java
public enum location {
        NORTH,
        EAST,
        SOUTH,
        WEST
}
```

## Spacing

Spacing is especially important as code needs to be easily readable.

### Indentation

Indentation is using tabs, __NEVER__ use spaces.


### Line Length

Lines should be no longer than 121 characters long.

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity and organization. Whitespace within methods should separate functionality, but having too many sections in a method often means you should refactor into several methods.

## Comments

When they are needed, use comments to explain **why** a particular piece of code does something. Comments must be kept up-to-date or deleted.

Avoid block comments inline with code, as the code should be as self-documenting as possible. *Exception: This does not apply to those comments used to generate documentation.*

## Getters & Setters

Only use a getter or a setter when these are needed.

## Brace Style

Only trailing closing-braces are awarded their own line. All others appear the same line as preceding code:

__BAD:__

```java
class MyClass
{
  private void doSomething()
  {
    if (someTest)
    {
      // ...
    }
    else
    {
      // ...
    }
  }
}
```

__GOOD:__

```java
class MyClass {
  private void doSomething() {
    if (someTest) {
      // ...
    } else {
      // ...
    }
  }
}
```

## Conditional Statements

Conditional statements are always required to be enclosed with braces, irrespective of the number of lines required.

__BAD:__

```kotlin
if (someTest)
  doSomething()
if (someTest) doSomethingElse()
```

__GOOD:__

```java
if (someTest) {
  doSomething();
}
if (someTest) { doSomethingElse(); }
```

## Switch Statements

If you are forced to use at least 2 `if else` statemants you need to consider hte use of a switch statement.

__BAD:__

```java
switch (anInput) {
  case 1:
      doSomethingForCaseOneOrTwo();
      break;
  case 2:
      doSomethingForCaseOneOrTwo();
      break;
  case 3:
      doSomethingForCaseThree();
      break;
}
```

__GOOD:__

```java
switch (anInput) {
  case 1:
  case 2:    
      doSomethingForCaseOneOrTwo();
      break;
  case 3:
      doSomethingForCaseThree();
      break;
  default:
      System.out.println("No case satisfied"); 
}
```





## XML Guidance

Since Android uses XML extensively in addition to Java, we have some rules
specific to XML.

### XML File Names

View-based XML files should be prefixed with the type of view that they
represent.

__BAD:__

- `login.xml`
- `main_screen.xml`
- `rounded_edges_button.xml`

__GOOD:__

- `activity_login.xml`
- `fragment_main_screen.xml`
- `button_rounded_edges.xml`

### XML Indentation

Similarly to Java, indentation should be __two tabs__.

### Use Context-Specific XML Files

Wherever possible XML resource files should be used:

- Strings => `res/values/strings.xml`
- Styles => `res/values/styles.xml`
- Colors => `res/color/colors.xml`
- Animations => `res/anim/`
- Drawable => `res/drawable`


### XML Attribute Ordering

Where appropriate, XML attributes should appear in the following order:

- `id` attribute
- `layout_*` attributes
- style attributes such as `gravity` or `textColor`
- value attributes such as `text` or `src`

Within each of these groups, the attributes should be ordered alphabetically.


## Language

Use US English spelling.

__BAD:__

```java
String colour = "red";
```

__GOOD:__

```java
String color = "red";
```

