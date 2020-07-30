---
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: fddfc2e3295552414a00692006ab12725dc07d52
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213115"
---
# <a name="void-c"></a>void (C++)

W przypadku użycia jako zwracanego typu funkcji **`void`** słowo kluczowe Określa, że funkcja nie zwraca wartości. W przypadku użycia dla listy parametrów funkcji **`void`** określa, że funkcja nie przyjmuje żadnych parametrów. Gdy jest używany w deklaracji wskaźnika, **`void`** określa, że wskaźnik jest "uniwersalny".

Jeśli typ wskaźnika to ** \* void**, wskaźnik może wskazywać wszelkie zmienne, które nie są zadeklarowane za pomocą **`const`** **`volatile`** słowa kluczowego or. Nie można usunąć odwołania do **pustego \* ** wskaźnika, chyba że jest rzutowany na inny typ. Wskaźnik **void \* ** można przekonwertować na dowolny inny typ wskaźnika danych.

**`void`** Wskaźnik może wskazywać na funkcję, ale nie do składowej klasy w języku C++.

Nie można zadeklarować zmiennej typu **`void`** .

## <a name="example"></a>Przykład

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy wbudowane](../cpp/fundamental-types-cpp.md)
