---
title: Błąd kompilatora C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 7cba9e0271d16420c5cfe4adbed2c7121d139d8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523926"
---
# <a name="compiler-error-c3539"></a>Błąd kompilatora C3539

"type": argument szablonu nie może być typem zawierającym "auto"

Typ argumentu wskazanego szablonu nie może zawierać użycie `auto` — słowo kluczowe.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie określaj argument szablonu, za pomocą `auto` — słowo kluczowe.

## <a name="example"></a>Przykład

Poniższy przykład daje C3539.

```
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

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)