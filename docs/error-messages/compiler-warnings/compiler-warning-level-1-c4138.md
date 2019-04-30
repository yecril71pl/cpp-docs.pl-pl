---
title: Kompilator ostrzeżenie (poziom 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: 96f8915b9bec166496ca4305d796ce8ef514ca15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402531"
---
# <a name="compiler-warning-level-1-c4138"></a>Kompilator ostrzeżenie (poziom 1) C4138

"* /" znaleziono poza komentarzem

Ogranicznik komentarza zamykający nie jest poprzedzony przez ogranicznik otwierający komentarz. Kompilator zakłada odstęp między gwiazdka (<strong>\**</strong>) i ukośnika (/).

## <a name="example"></a>Przykład

```
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

To ostrzeżenie może być spowodowany próby zagnieździć komentarzy.

Mogą być rozwiązane to ostrzeżenie, jeśli komentarz wystąpi poza sekcje kodu zawierające komentarze, należy wpisać kod w **#if / #endif** zablokować, a wyrażenie kontrolujące należy ustawić na zero:

```
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```