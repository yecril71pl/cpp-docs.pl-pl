---
title: Kompilator ostrzeżenie (poziom 1) C4138 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2e637c73482b1a59034d6a269ea2240445bdef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046917"
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