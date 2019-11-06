---
title: Ostrzeżenie kompilatora (poziom 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e6e368f27371b744efa4006630938f68f51a2ca0
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627096"
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