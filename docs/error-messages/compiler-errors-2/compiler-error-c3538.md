---
title: Błąd kompilatora C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: e8b97c8c6e5d23c406bf2d5831279810e7de0902
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035033"
---
# <a name="compiler-error-c3538"></a>Błąd kompilatora C3538

na liście deklaratorów "auto" należy zawsze ustalać do tego samego typu

Wszystkie zmienne zadeklarowane na liście deklaracji nie rozwiązują tego samego typu.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że wszystkie `auto` deklaracje na liście ustalane do tego samego typu.

## <a name="example"></a>Przykład

Poniższe instrukcje yield C3538. Każda instrukcja deklaruje wiele zmiennych, ale każde użycie `auto` — słowo kluczowe nie być ustalane do tego samego typu.

```
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)