---
title: Błąd kompilatora C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 95ca5ea846f9cd45bdb1e9706ae377589d37a285
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756022"
---
# <a name="compiler-error-c2665"></a>Błąd kompilatora C2665

"Function": żadne z przeciążeń Liczba1 nie może konwertować parametru liczba2 z typu "Type"

Nie można przekonwertować parametru przeciążonej funkcji na wymagany typ.  Możliwe rozwiązania:

- Podaj Operator konwersji.

- Użyj konwersji jawnej.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2665.

```cpp
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```
