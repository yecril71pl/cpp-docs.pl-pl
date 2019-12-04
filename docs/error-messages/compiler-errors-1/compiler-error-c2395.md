---
title: Błąd kompilatora C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: 2ac59856770b04dd3c4ea14360e0a83dd99f2150
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744943"
---
# <a name="compiler-error-c2395"></a>Błąd kompilatora C2395

"your_type:: operator'op" ": nieprawidłowy operator CLR lub WinRT. Co najmniej jeden parametr musi mieć następujące typy: "t", "t%", "&", "^", "^%", "^ &", gdzie T = "your_type"

Operator w środowisko wykonawcze systemu Windows lub typie zarządzanym nie ma co najmniej jednego parametru, którego typ jest taki sam jak typ zwracanej wartości operatora.

Poniższy przykład generuje C2395 i pokazuje, jak to naprawić:

```cpp
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```
