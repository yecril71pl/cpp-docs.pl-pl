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
ms.openlocfilehash: fbb9c45ec816c859edb4df38ad67dc7778247e87
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537765"
---
# <a name="module-import-export"></a>moduł, import, eksport

Słowa kluczowe **modułu**, **importu**i **eksportu** są dostępne w `/experimental:modules` języku c++ 20 i wymagają przełącznika kompilatora wraz z. `/std:c++latest` Aby uzyskać więcej informacji, zobacz [Omówienie modułów w C++ ](modules-cpp.md)temacie.

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
