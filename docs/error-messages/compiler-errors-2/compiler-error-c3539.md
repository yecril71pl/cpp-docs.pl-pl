---
title: Błąd kompilatora C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 85381b237480b86b59c33f02601a1b9dc644a5a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761533"
---
# <a name="compiler-error-c3539"></a>Błąd kompilatora C3539

"Type": argument szablonu nie może być typem zawierającym wartość "Auto"

Wskazany typ argumentu szablonu nie może zawierać użycia słowa kluczowego `auto`.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie określaj argumentu szablonu za pomocą słowa kluczowego `auto`.

## <a name="example"></a>Przykład

Poniższy przykład daje C3539.

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)
