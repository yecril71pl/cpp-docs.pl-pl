---
title: moduł, import, eksport
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Użyj deklaracji importu i eksportu, aby uzyskać dostęp do typów i funkcji, które są zdefiniowane w określonym module, oraz do ich publikowania.
ms.openlocfilehash: 7406bf75595bef20775ee1b67c27bd62bff1a932
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518286"
---
# <a name="module-import-export"></a>moduł, import, eksport

Deklaracje **modułu**, **importu**i **eksportu** są dostępne w języku c++ 20 i wymagają przełącznika kompilatora [/Experimental: modułu](../build/reference/experimental-module.md) z [/std: C + + Najnowsza](../build/reference/std-specify-language-standard-version.md). Aby uzyskać więcej informacji, zobacz [Omówienie modułów w C++ ](modules-cpp.md)temacie.

## <a name="module"></a>moduł

Umieść deklarację **modułu** na początku pliku implementacji modułu, aby określić, że zawartość pliku należy do nazwanego modułu.

```cpp
module ModuleA;
```

## <a name="export"></a>export

Użyj deklaracji **modułu eksportu** dla podstawowego pliku interfejsu modułu, który musi mieć rozszerzenie **. IXX**:

```cpp
export module ModuleA;
```

W pliku interfejsu Użyj modyfikatora **eksportu** dla nazw, które mają być częścią interfejsu publicznego:

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

Nieeksportowane nazwy nie są widoczne dla kodu, który importuje moduł:

```cpp
//MyProgram.cpp

import module ModuleA;

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Słowo kluczowe **Export** może nie pojawić się w pliku implementacji modułu. Po zastosowaniu **eksportu** do nazwy przestrzeni nazw wszystkie nazwy w przestrzeni nazw są eksportowane.

## <a name="import"></a>import

Użyj deklaracji **importu** , aby uczynić nazwy modułów widocznymi w programie. Deklaracja importu musi znajdować się po deklaracji modułu i po każdej #include dyrektywie, ale przed wszelkimi deklaracjami w pliku.

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="remarks"></a>Uwagi

Zarówno **Import** , jak i **moduł** są traktowane jako słowa kluczowe, gdy pojawiają się na początku linii logicznej:

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**Microsoft Specific**

W firmie C++Microsoft tokeny **importu** i **modułu** są zawsze identyfikatory i nigdy nie są słowami kluczowymi, gdy są używane jako argumenty do makra.

### <a name="example"></a>Przykład

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Zakończenie określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Przegląd modułów w programieC++](modules-cpp.md)
