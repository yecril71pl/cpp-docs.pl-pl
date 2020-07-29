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
ms.openlocfilehash: 5be1618d7e64f6887cf78bd863d428d6710eaf7e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187195"
---
# <a name="module-import-export"></a>moduł, import, eksport

**Moduł**, **Importowanie**i **`export`** deklaracje są dostępne w języku c++ 20 i wymagają przełącznika kompilatora [/Experimental: module](../build/reference/experimental-module.md) z [/std: C + + Najnowsza](../build/reference/std-specify-language-standard-version.md). Aby uzyskać więcej informacji, zobacz [Omówienie modułów w języku C++](modules-cpp.md).

## <a name="module"></a>moduł

Umieść deklarację **modułu** na początku pliku implementacji modułu, aby określić, że zawartość pliku należy do nazwanego modułu.

```cpp
module ModuleA;
```

## <a name="export"></a>eksportowanie

Użyj deklaracji **modułu eksportu** dla podstawowego pliku interfejsu modułu, który musi mieć rozszerzenie **. IXX**:

```cpp
export module ModuleA;
```

W pliku interfejsu, użyj **`export`** modyfikatora w nazwach, które są przeznaczone do interfejsu publicznego:

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

**`export`** Słowo kluczowe może nie pojawić się w pliku implementacji modułu. Gdy **`export`** jest stosowany do nazwy przestrzeni nazw, zostaną wyeksportowane wszystkie nazwy w przestrzeni nazw.

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

**Specyficzne dla firmy Microsoft**

W programie Microsoft C++ tokeny **importu** i **modułu** są zawsze identyfikatory i nigdy nie są słowami kluczowymi, gdy są używane jako argumenty do makra.

### <a name="example"></a>Przykład

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Zakończenie określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Omówienie modułów w języku C++](modules-cpp.md)
