---
title: initonly (C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: 91b1447231cbc189a701517e48890fea34c2858a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742894"
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

[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)
