---
title: initonly (C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: cdfc278225ce4ab418dfaaf41fb413d088ad77df
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58766577"
---
# <a name="initonly-ccli"></a>initonly (C++/CLI)

**InitOnly** jest kontekstowe słowo kluczowe, która wskazuje, że przypisanie zmiennej jest możliwe tylko w ramach deklaracji lub w konstruktorze statycznym w tej samej klasie.

Poniższy przykład pokazuje, jak używać `initionly`:

```
// mcpp_initonly.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst1;

   initonly
   static int staticConst2 = 0;

   static Y1() {
      staticConst1 = 0;
   }
};
```

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
