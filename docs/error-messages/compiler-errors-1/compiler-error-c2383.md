---
title: Błąd kompilatora C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: e9c1774fe7cd4a6883aa79f384cc64521a57ed17
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448009"
---
# <a name="compiler-error-c2383"></a>Błąd kompilatora C2383

"*symbol*": argumenty domyślne nie są dozwolone w tym symbolu

Kompilator języka C++ nie zezwala na wskaźniki do funkcji argumenty domyślne.

Ten kod został zaakceptowany przez firmę Microsoft C++ kompilatora w wersjach starszych niż program Visual Studio 2005, ale teraz powoduje błąd. Kod, który działa we wszystkich wersjach programu Visual C++ nie należy przypisywać wartość domyślna argumentu wskaźnika do funkcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2383 i przedstawiono możliwe rozwiązania:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```