---
layout: post
title: "Python for Ruby Developers: A Comparison Guide"
date: 2024-10-09
categories: Python
---

# **🐍 Python for Ruby Developers: A Comparison Guide**

This guide highlights the core differences between Python and Ruby, focusing on concepts familiar to a Ruby developer. The goal is to provide a quick reference for adapting your thinking and syntax.

| Concept | Ruby | Python |
| :---- | :---- | :---- |
| **Syntax** | Block-based with `do...end` or `{}`. Indentation is for readability. Optional parentheses for method calls. | Indentation-based, where whitespace defines blocks. Colons `(:)` are required for `if, for, def,` etc. |
| **String Interpolation** | Uses `\#{variable}` inside double-quoted strings. | Uses `f-strings (f"hello {variable}")` or the `.format()` method. |
| **Lists & Arrays** | An Array is the primary ordered collection. | A `list` is the primary ordered collection. A `tuple` is an immutable (unchangeable) version of a list. |
| **Hashes & Dictionaries** | A `Hash` is an unordered key-value collection, often using symbols as keys `({key: 'value'})`. | A `dict (dictionary)` is an unordered key-value collection, often using strings as keys` ({'key': 'value'})`. |
| **Falsy Values** | `false` and `nil` are the only `falsy` values. Everything else is `truthy`. | `False, None, empty collections (\[\], {}, (), '')`, and the` number 0` are all `falsy`. |
| **Methods & Functions** | Defined with `def`, ended with `end`. `return` is optional. Blocks are passed implicitly. | Defined with `def`, ended with `indentation`. `return` is optional, but often used for clarity. Callables are functions, not methods on objects by default. |
| **Inheritance** | Uses the `<` operator in the class definition. | Uses parentheses `()` in the class definition. |
| **Constants** | Uppercase names are `constants`, but a warning is issued if they are reassigned. | No true constants. All-uppercase names `(CONST\_NAME)` are a convention to signify a variable should not be changed. In Python, a variable intended to be a constant is written in ALL_CAPS. For example, PI = 3.14159. This is a signal to other developers that the value should not be changed. However, unlike Ruby, which issues a warning if you try to reassign a constant, the Python interpreter will not prevent you from modifying the value. |
| **Package Management** | Bundler manages gems via a `Gemfile.` | `pipenv` manages packages via a `Pipfile` and `Pipfile.lock`. `pip` and `requirements.txt` are also very common. |
| **Class Syntax** | `class MyClass, end.` Instance variables use`@variable`. | `class MyClass:` Instance variables are defined with `self.variable` in the `__init__` method. |
| **Looping** | `each, map, collect, times` are methods on objects. | `for` loops iterate over any iterable. List comprehensions `x for x in list` are a very common Pythonic pattern. |
| **Method Visibility** | `public, private, protected.` | All methods are `public` by default. Use a leading underscore `_method` by convention for `"private"` methods, or double underscores `__method` for `name-mangling.` |
| **Testing** | `RSpec` and `Minitest` are popular. | `Pytest` and `unittest` are popular.|
