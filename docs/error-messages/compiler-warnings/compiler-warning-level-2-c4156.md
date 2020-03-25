---
title: Ostrzeżenie kompilatora (poziom 2) C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: b9add4af0fddf8d68bbba0293530f2bb0ce3800d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162091"
---
# <a name="compiler-warning-level-2-c4156"></a>Ostrzeżenie kompilatora (poziom 2) C4156

usunięcie wyrażenia tablicowego bez użycia formularza tablicy "Delete"; zastąpiono formularz tablicy

Forma nie będąca tablicą elementu **delete** nie może usunąć tablicy. Kompilator **przetłumaczy** do formularza tablicy.

To ostrzeżenie występuje tylko w ramach rozszerzeń Microsoft (/ze).

## <a name="example"></a>Przykład

```cpp
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```
