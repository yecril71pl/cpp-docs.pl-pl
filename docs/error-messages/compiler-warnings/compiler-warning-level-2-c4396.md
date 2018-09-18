---
title: Kompilator ostrzeżenie (poziom 2) C4396 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa0a084e90db9d48f517bfe65c6340eb532f0ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118573"
---
# <a name="compiler-warning-level-2-c4396"></a>Kompilator ostrzeżenie (poziom 2) C4396

"name": wbudowany specyfikator nie można użyć, gdy zaprzyjaźniona deklaracja odnosi się do specjalizacji szablonu funkcji

Specjalizacja szablonu funkcji nie można określić dowolną z [wbudowane](../../cpp/inline-functions-cpp.md) specyfikatorów. Kompilator generuje ostrzeżenie C4396 i ignoruje wbudowany specyfikator.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń `inline`, `__inline`, lub `__forceinline` specyfikator w deklaracji funkcji friend.

## <a name="example"></a>Przykład

Nieprawidłowy friend funkcji deklaracji z ilustruje poniższy przykład kodu `inline` specyfikator.

```
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```