---
title: Ostrzeżenie kompilatora (poziom 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e1f28f5afb1879229ff0d408cb576312966e1c81
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200112"
---
# <a name="compiler-warning-level-1-c4138"></a>Ostrzeżenie kompilatora (poziom 1) C4138

znaleziono "*/" poza komentarzem

Ogranicznik komentarza zamykającego nie jest poprzedzony ogranicznikiem otwierającym komentarz. Kompilator zakłada miejsce między gwiazdką (<strong>\*</strong>) i ukośnikiem (/).

## <a name="example"></a>Przykład

```cpp
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

To ostrzeżenie może być spowodowane próbą zazagnieżdżania komentarzy.

To ostrzeżenie można rozwiązać w przypadku dodawania komentarzy do sekcji kodu, które zawierają komentarze, należy ująć kod w bloku **#if/#endif** i ustawić wyrażenie kontrolne na wartość zero:

```cpp
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```
