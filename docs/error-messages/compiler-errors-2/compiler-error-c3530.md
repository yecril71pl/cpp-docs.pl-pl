---
title: Błąd kompilatora C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: dd4368faaf323a75116128ec3a47666260436fce
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029122"
---
# <a name="compiler-error-c3530"></a>Błąd kompilatora C3530

"auto" nie można łączyć z jakimkolwiek innym specyfikatorem typu

Specyfikator typu jest używana z `auto` — słowo kluczowe.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie należy używać specyfikatora typu w deklaracji zmiennej, która używa `auto` — słowo kluczowe.

## <a name="example"></a>Przykład

Poniższy przykład daje C3530, ponieważ zmienna `x` jest zadeklarowana za pomocą obu `auto` słów kluczowych i typów `int`, a ponieważ przykładu jest kompilowany przy użyciu **/Zc: Auto**.

```
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)