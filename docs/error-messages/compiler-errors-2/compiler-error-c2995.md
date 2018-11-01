---
title: Błąd kompilatora C2995
ms.date: 11/04/2016
f1_keywords:
- C2995
helpviewer_keywords:
- C2995
ms.assetid: a57cdfe0-b40b-4a67-a95c-1a49ace4842b
ms.openlocfilehash: 56bd012457fe17cec7d46095ba7c98658d030b14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557506"
---
# <a name="compiler-error-c2995"></a>Błąd kompilatora C2995

'Funkcja': szablon funkcji został już zdefiniowany

Upewnij się, że istnieje tylko jedną definicję dla każdej funkcji składowej klasy oparte na szablonach.

Poniższy przykład spowoduje wygenerowanie C2995:

```
// C2995.cpp
// compile with: /c
template <class T>
void Test(T x){}

template <class T> void Test(T x){}   // C2995
template <class T> void Test2(T x){}   // OK
```