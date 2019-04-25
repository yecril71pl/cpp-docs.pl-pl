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
ms.openlocfilehash: cb4be000c3c41862d5b4df766d21ae1cddeb6838
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243994"
---
# <a name="void-c"></a>void (C++)

Gdy jest używana jako zwracany typ funkcji, **void** — słowo kluczowe Określa, że funkcja nie zwraca wartości. Gdy jest używana dla listy wartości parametru funkcji void Określa, że funkcja nie przyjmuje żadnych parametrów. W przypadku użycia w deklaracji wskaźnika, typ void Określa, że wskaźnik "uniwersalne".

Jeśli typ wskaźnika `void *`, wskaźnik może wskazywać jakakolwiek zmienna, która nie jest zadeklarowana za pomocą **const** lub **volatile** — słowo kluczowe. Nie można usunąć odwołania wskaźnika void, chyba że jest rzutowane do innego typu. Dowolny inny typ wskaźnika danych, można przekonwertować na wskaźnik typu void.

Pusty wskaźnik może wskazywać na funkcję, ale nie do składowej klasy w języku C++.

Nie można zadeklarować zmienną typu void.

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
[Typy podstawowe](../cpp/fundamental-types-cpp.md)