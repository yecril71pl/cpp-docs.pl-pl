---
title: Błąd kompilatora C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: e30ea0713229bfd8da395baef710571f8dfd49e9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508149"
---
# <a name="compiler-error-c3539"></a>Błąd kompilatora C3539

"Type": argument szablonu nie może być typem zawierającym wartość "Auto"

Wskazany typ argumentu szablonu nie może zawierać użycia **`auto`** słowa kluczowego.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie określaj argumentu szablonu ze **`auto`** słowem kluczowym.

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

## <a name="see-also"></a>Zobacz też

[Słowo kluczowe "Autouzupełnianie"](../../cpp/auto-cpp.md)
