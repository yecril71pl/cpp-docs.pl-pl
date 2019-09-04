---
title: moduł, import, eksport
ms.date: 07/15/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Użyj instrukcji import, aby uzyskać dostęp do typów i funkcji zdefiniowanych w określonym module.
ms.openlocfilehash: ee1d50a76a3304359c0771aa0174968439f5faa4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273624"
---
# <a name="module-import-export"></a>moduł, import, eksport

Słowa kluczowe **modułu**, **importu**i **eksportu** są dostępne w języku c++ 20 i wymagają przełącznika kompilatora [/Experimental: modułu](../build/reference/experimental-module.md) z [/std: C + + Najnowsza](../build/reference/std-specify-language-standard-version.md). Aby uzyskać więcej informacji, zobacz [Omówienie modułów w C++ ](modules-cpp.md)temacie.

## <a name="module"></a>moduł

Użyj instrukcji **module** na początku pliku implementacji modułu, aby określić, że zawartość pliku należy do nazwanego modułu. 

```cpp
module ModuleA;
```

## <a name="export"></a>export

Użyj instrukcji **Export module** dla podstawowego pliku interfejsu modułu, który musi mieć rozszerzenie **. IXX**:

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

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Słowo kluczowe **Export** może nie pojawić się w pliku implementacji modułu. Gdy modyfikator **eksportu** zostanie zastosowany do nazwy przestrzeni nazw, zostaną wyeksportowane wszystkie nazwy w przestrzeni nazw.

## <a name="import"></a>import

Użyj instrukcji **Import** , aby w programie były widoczne nazwy modułów. Instrukcja import musi występować po instrukcji modułu i po każdej #include dyrektywie, ale przed wszelkimi deklaracjami w pliku.

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

## <a name="see-also"></a>Zobacz też

[Przegląd modułów w programieC++](modules-cpp.md)
