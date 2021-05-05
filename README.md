# nenya

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Language](https://img.shields.io/badge/C%2B%2B-20-blue.svg)](https://en.wikipedia.org/wiki/C%2B%2B#Standardization)
[![CI: Windows](https://github.com/albin-johansson/nenya/actions/workflows/windows.yml/badge.svg?branch=dev)](https://github.com/albin-johansson/nenya/actions/workflows/windows.yml)

A small but powerful library for creating strong types, written in C++20.

## Usage

You can use nenya to create strong types, i.e. types that behave pretty much exactly as another type, whilst being a unique type to the compiler. This is extremely useful to avoid hard to find errors, such as passing arguments of the same type in the wrong order, etc. This library can produce strong types that inherit almost all operators of the underlying type.

```C++

#include <nenya.hpp>

// This isn't strictly necessary, but it avoids confusing intellisense.
namespace tags {
struct row_tag;
struct col_tag;
struct name_tag;
}

// Strong types for row and column indices
using row_t = nenya::strong_type<int, tags::row_tag>;
using col_t = nenya::strong_type<int, tags::col_tag>;

// Also works for non-primitive types
using name_t = nenya::strong_type<std::string, tags::name_tag>;

// Strong types help with creating expressive and unambiguous interfaces
void foo(row_t row, col_t column)
{
  // ...
}

void bar()
{
  row_t row{42};
  col_t col{123};

  foo(row, col);  // Fine!
  // foo(col, row);  // Won't compile, this would normally be a subtle bug!

  name_t name{"Gandalf"};

  // Call member functions of the underlying type
  const auto size = name->size();
  auto& ch = name[0];
}

```
