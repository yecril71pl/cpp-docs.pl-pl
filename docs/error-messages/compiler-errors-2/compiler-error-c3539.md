---
title: Błąd kompilatora C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: be1051859ebbcbdc22a9b71f8c5adba2e75c4e92
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025183"
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

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)