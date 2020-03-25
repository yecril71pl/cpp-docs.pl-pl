---
title: Błąd kompilatora C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 4c87e98f11a560d0d92be8ea7bc624edd4e09ad2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201399"
---
# <a name="compiler-error-c3286"></a>Błąd kompilatora C3286

> "*specyfikator*": Zmienna iteracji nie może mieć żadnych specyfikatorów klasy magazynu

Nie można określić klasy magazynu dla zmiennej iteracji. Aby uzyskać więcej informacji, zobacz [klasy magazynuC++()](../../cpp/storage-classes-cpp.md) i [dla każdego z nich w](../../dotnet/for-each-in.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3286, a także wyświetla poprawne użycie.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
