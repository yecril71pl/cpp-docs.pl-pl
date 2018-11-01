---
title: Błąd kompilatora C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: fcf2bbb01f2aac668ff52884a6ccfb36c66aa89d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445843"
---
# <a name="compiler-error-c2785"></a>Błąd kompilatora C2785

"declaration1" i "declaration2" mają różne typy zwracane

Zwracany typ specjalizacja szablonu funkcji różni się od zwracany typ szablonu podstawowej funkcji.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź wszystkie specjalizacje szablonu funkcji w celu zachowania spójności.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2785:

```
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```