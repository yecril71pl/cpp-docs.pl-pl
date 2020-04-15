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
description: Użyj deklaracji importu i eksportu, aby uzyskać dostęp i publikować typy i funkcje zdefiniowane w określonym module.
ms.openlocfilehash: a765e9a406660d3c945ef3d70754178b0648458c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374118"
---
# <a name="module-import-export"></a>moduł, import, eksport

**Moduł**, **import**i deklaracje **eksportowe** są dostępne w języku C++20 i wymagają przełącznika kompilatora [/experimental:module](../build/reference/experimental-module.md) wraz z [/std:c++latest](../build/reference/std-specify-language-standard-version.md). Aby uzyskać więcej informacji, zobacz [Omówienie modułów w języku C++](modules-cpp.md).

## <a name="module"></a>moduł

Umieść deklarację **modułu** na początku pliku implementacji modułu, aby określić, że zawartość pliku należy do nazwanego modułu.

```cpp
module ModuleA;
```

## <a name="export"></a>export

Użyj deklaracji **modułu eksportu** dla pliku interfejsu podstawowego modułu, który musi mieć rozszerzenie **.ixx:**

```cpp
export module ModuleA;
```

W pliku interfejsu użyj modyfikatora **eksportu** na nazwach, które mają być częścią interfejsu publicznego:

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

Słowo kluczowe **eksportu** może nie pojawić się w pliku implementacji modułu. Gdy **eksport** jest stosowany do nazwy obszaru nazw, wszystkie nazwy w obszarze nazw są eksportowane.

## <a name="import"></a>import

Użyj deklaracji **importu,** aby nazwy modułu były widoczne w programie. Deklaracja importu musi pojawić się po deklaracji modułu i po wszelkich #include dyrektyw, ale przed wszelkimi deklaracjami w pliku.

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

Zarówno **import,** jak i **moduł** są traktowane jako słowa kluczowe tylko wtedy, gdy pojawiają się na początku wiersza logicznego:

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

**Specyficzne dla firmy Microsoft**

W języku Microsoft C++ **import** tokenów i **moduł** są zawsze identyfikatory i nigdy słowa kluczowe, gdy są one używane jako argumenty do makra.

### <a name="example"></a>Przykład

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Koniec z programem Microsoft**

## <a name="see-also"></a>Zobacz też

[Omówienie modułów w języku C++](modules-cpp.md)
