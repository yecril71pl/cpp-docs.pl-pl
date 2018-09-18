---
title: Błąd kompilatora C2383 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c529c22636f112291fa53b852899cad78dac589
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113230"
---
# <a name="compiler-error-c2383"></a>Błąd kompilatora C2383

"*symbol*": argumenty domyślne nie są dozwolone w tym symbolu

Kompilator języka C++ nie zezwala na wskaźniki do funkcji argumenty domyślne.

Ten kod został zaakceptowany przez kompilator języka Visual C++ w wersjach starszych niż program Visual Studio 2005, ale teraz powoduje błąd. Kod, który działa we wszystkich wersjach programu Visual C++ nie należy przypisywać wartość domyślna argumentu wskaźnika do funkcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2383 i przedstawiono możliwe rozwiązania:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```