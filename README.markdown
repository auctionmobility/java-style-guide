# The Official Auction Mobility Java Style Guide forked from https://github.com/raywenderlich/java-style-guide and adopted a bit.

## Table of Contents

- [Nomenclature](#nomenclature)
  + [Packages](#packages)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Variables & Parameters](#variables--parameters)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Enum Classes](#enum-classes)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Getters & Setters](#getters--setters)
- [Brace Style](#brace-style)
- [Switch Statements](#switch-statements)
- [Annotations](#annotations)
- [XML Guidance](#xml-guidance)
  + [XML File Names](#xml-file-names)
  + [Indentation](#indentation-1)
  + [Use Context-Specific XML Files](#use-context-specific-xml-files)
  + [XML Attribute Ordering](#xml-attribute-ordering)
- [Language](#language)
- [Copyright Statement](#copyright-statement)
- [Smiley Face](#smiley-face)
- [Credit](#credits)


## Nomenclature

On the whole, naming should follow Java standards.

### Packages

Package names are all __lower-case__, multiple words concatenated together,
without
hypens or underscores:

__BAD__:

```java
com.RayWenderlich.funky_widget
```

__GOOD__:

```java
com.raywenderlich.funkywidget
```

### Classes & Interfaces

Written in __UpperCamelCase__. For example `RadialSlider`. 

### Methods

Written in __lowerCamelCase__. For example `setValue`.

### Fields

Written in __lowerCamelCase__.

Static fields should be written in __uppercase__, with an underscore separating
words:

```java
public static final int THE_ANSWER = 42;
```

Fields naming example:

```java
public class MyClass {
  public static final int SOME_CONSTANT = 42;
  public int publicField;
  private static MyClass singleton;
  int packagePrivate;
  private int private;
  protected int protected;
}
```

### Variables & Parameters

Written in __lowerCamelCase__.

Single character values to be avoided except for temporary looping variables.

### Misc

In code, acronyms should be treated as words. For example:

__BAD:__

```java
XMLHTTPRequest
String URL
findPostByID
```
__GOOD:__

```java
XmlHttpRequest
String url
findPostById
```

## Declarations

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and
member variables.

### Fields & Variables

Prefer single declaration per line.

__BAD:__

```java
String username, twitterHandle;
```

__GOOD:__

```java
String username;
String twitterHandle;
```

### Classes

Exactly one class per source file, although inner classes are encouraged where
scoping appropriate.


### Enum Classes

Enum classes should be avoided where possible, due to a large memory overhead.
Static constants are preferred. See http://developer.android.com/training/articles/memory.html#Overhead
for further details.

Enum classes without methods may be formatted without line-breaks, as follows:

```java
private enum CompassDirection { EAST, NORTH, WEST, SOUTH }
```

## Spacing and indentation

Indentation is using spaces - never tabs.

#### Blocks

Indentation for blocks uses 4 spaces:

__BAD:__

```java
for (int i = 0; i < 10; i++) {
  Log.i(TAG, "index=" + i);
}
```

__GOOD:__

```java
for (int i = 0; i < 10; i++) {
    Log.i(TAG, "index=" + i);
}
```

#### Line Wraps

Indentation for line wraps should use 4 spaces (not the default 8):

__BAD:__

```java
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

__GOOD:__

```java
CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

### Line Length

Lines should be no longer than 120 characters long.


### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity 
and organization. Whitespace within methods should separate functionality, but 
having too many sections in a method often means you should refactor into
several methods.

## Getters & Setters

For external access to fields in classes, getters and setters are preferred to
direct access of the fields. Fields should rarely be `public`.

However, it is encouraged to use the field directly when accessing internally
(i.e. from inside the class). This is a performance optimization recommended
by Google: http://developer.android.com/training/articles/perf-tips.html#GettersSetters

## Brace Style

Only trailing closing-braces are awarded their own line. All others appear the
same line as preceding code:

__BAD:__

```java
class MyClass
{
  void doSomething()
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
  void doSomething() {
    if (someTest) {
      // ...
    } else {
      // ...
    }
  }
}
```

Conditional statements are always required to be enclosed with braces,
irrespective of the number of lines required.

__BAD:__

```java
if (someTest)
  doSomething();
if (someTest) doSomethingElse();
```

__GOOD:__

```java
if (someTest) {
  doSomething();
}
if (someTest) { doSomethingElse(); }
```


## Switch Statements

Switch statements fall-through by default, but this can be unintuitive. If you
require this behavior, comment it.

Alway include the `default` case.

__BAD:__

```java
switch (anInput) {
  case 1:
    doSomethingForCaseOne();
  case 2:
    doSomethingForCaseOneOrTwo();
    break;
  case 3:
    doSomethingForCaseOneOrThree();
    break;
}
```

__GOOD:__

```java
switch (anInput) {
  case 1:
    doSomethingForCaseOne();
    // fall through
  case 2:
    doSomethingForCaseOneOrTwo();
    break;
  case 3:
    doSomethingForCaseOneOrThree();
    break;
  default:
    break;
}
```

## Annotations

Standard annotations should be used - in particular `@Override`. This should
appear the line before the function declaration.

__BAD:__

```java
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
}
```

__GOOD:__

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
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

### Indentation

Similarly to Java, indentation should be __four characters__.

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
