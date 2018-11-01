---
title: Błąd kompilatora C2953
ms.date: 11/04/2016
f1_keywords:
- C2953
helpviewer_keywords:
- C2953
ms.assetid: 8dbcfa24-8296-4e40-bdc4-5526c07d8892
ms.openlocfilehash: 8fa0e533b23f735f948fdad0ecf11beb3766f452
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591054"
---
# <a name="compiler-error-c2953"></a>Błąd kompilatora C2953

'Identyfikator': szablon klasy została już zdefiniowana

Sprawdź plik źródłowy, a następnie Dołącz pliki dla inne definicje.

Poniższy przykład spowoduje wygenerowanie C2953:

```
// C2953.cpp
// compile with: /c
template <class T>  class A {};
template <class T>  class A {};   // C2953
template <class T>  class B {};   // OK
```