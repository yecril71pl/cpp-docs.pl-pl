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
ms.openlocfilehash: 8a2c74e9ace77e38587209a0ad6fdc03b07cc3ad
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301759"
---
# <a name="void-c"></a>void (C++)

W przypadku użycia jako zwracanego typu funkcji **void** słowo kluczowe Określa, że funkcja nie zwraca wartości. W przypadku użycia dla listy parametrów funkcji **void** określa, że funkcja nie przyjmuje żadnych parametrów. Gdy jest używany w deklaracji wskaźnika, **void** określa, że wskaźnik jest "uniwersalny".

Jeśli typ wskaźnika to **void\*** , wskaźnik może wskazywać wszelkie zmienne, które nie są zadeklarowane za pomocą słowa kluczowego **const** lub **volatile** . Nie można usunąć odwołania do wskaźnika **void\*** , chyba że jest on rzutowany na inny typ. Wskaźnik **\*void** można przekonwertować na dowolny inny typ wskaźnika danych.

Wskaźnik **void** może wskazywać na funkcję, ale nie do elementu członkowskiego klasy w C++.

Nie można zadeklarować zmiennej typu **void**.

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

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy wbudowane](../cpp/fundamental-types-cpp.md)