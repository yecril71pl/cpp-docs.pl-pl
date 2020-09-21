---
title: Błąd kompilatora C2897
ms.date: 11/04/2016
f1_keywords:
- C2897
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
ms.openlocfilehash: 22e63ce92a6d526f08e68bedb35de104be339dc3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743376"
---
# <a name="compiler-error-c2897"></a>Błąd kompilatora C2897

destruktor/finalizator nie może być szablonem funkcji

Destruktory i finalizatory nie mogą być przeciążone, dlatego deklarując destruktor jako szablon (który definiuje zestaw destruktorów) jest niedozwolony.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2897.

```cpp
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

Poniższy przykład generuje C2897.

```cpp
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```
