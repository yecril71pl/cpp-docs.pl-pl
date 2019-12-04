---
title: Błąd kompilatora C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: 6aff2e5c96e3c79fc748d8a95779d6a08647ab03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739626"
---
# <a name="compiler-error-c2785"></a>Błąd kompilatora C2785

"declaration1" i "declaration2" mają różne typy zwracane

Typ zwracany specjalizacji szablonu funkcji różni się od typu zwracanego podstawowego szablonu funkcji.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź wszystkie specjalizacje szablonu funkcji pod kątem spójności.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2785:

```cpp
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
