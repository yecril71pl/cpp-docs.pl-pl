---
title: Ostrzeżenie C4730 kompilatora (poziom 1)
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: 4da60194deaeac3c79f8c3e9be3bd87d91bc7ca2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386359"
---
# <a name="compiler-warning-level-1-c4730"></a>Ostrzeżenie C4730 kompilatora (poziom 1)

"main": połączenie typu _m64 i zmiennoprzecinkowa wyrażeń może spowodować niepoprawny kod

Funkcja używa [__m64](../../cpp/m64.md) i **float**/**double** typów. Ponieważ MMX i rejestrów zmiennoprzecinkowych współużytkować ten sam fizyczny przestrzeń rejestru (nie można jednocześnie używać), za pomocą `__m64` i **float**/**double** typy w tym samym funkcja może spowodować uszkodzenie danych, prawdopodobnie jest przyczyną wyjątku.

Aby bezpiecznie korzystać z `__m64` typów i typów zmiennoprzecinkowych w tej samej funkcji każdej instrukcji, która korzysta z jednego z typów powinny być oddzielone **_m_empty()** (w przypadku MMX) lub **_m_femms()** (w przypadku 3DNow!) wewnętrzne.

Poniższy przykład spowoduje wygenerowanie C4730:

```
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```