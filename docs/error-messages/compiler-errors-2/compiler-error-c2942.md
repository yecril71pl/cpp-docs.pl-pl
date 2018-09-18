---
title: Błąd kompilatora C2942 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2942
dev_langs:
- C++
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 024557750def49151d835545eec62bfc6f4727e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033202"
---
# <a name="compiler-error-c2942"></a>Błąd kompilatora C2942

"class": typ klasy identyfikator ponownie definiowana jako argument formalny funkcji

Generyczny lub szablonu klasy nie można użyć jako argumentu formalnego. Nie można przekazać argument bezpośrednio do konstruktora ogólnego lub klasą szablonu.

Poniższy przykład spowoduje wygenerowanie C2942:

```

// C2942.cpp
// compile with: /c
template<class T>
struct TC {};
void f(int TC<int>) {}   // C2942

// OK
struct TC2 {};
void f(TC2 i) {}
```

C2942 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2942b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
void f(int GC<int>) {}   // C2942
ref struct GC2 { };
void f(int GC2) {}
```