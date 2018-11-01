---
title: Kompilator ostrzeżenie (poziom 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: c585294686298a1197d437d41a0d541f1268985f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512739"
---
# <a name="compiler-warning-level-3-c4290"></a>Kompilator ostrzeżenie (poziom 3) C4290

Zignorowano z wyjątkiem sygnalizacji funkcji specyfikację wyjątku C++ nie jest __declspec(nothrow)

Funkcja jest zadeklarowana za pomocą Specyfikacja wyjątku, który akceptuje Visual C++, ale nie implementuje. Kod wyjątku, potrzebnych specyfikacje, które są ignorowane podczas kompilacji mogą być ponownie kompilowane i połączone jako ponownie w przyszłych wersjach Obsługa specyfikacje wyjątków.

Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Można uniknąć tego ostrzeżenia, używając [ostrzeżenie](../../preprocessor/warning.md) pragmy:

```
#pragma warning( disable : 4290 )
```

Poniższy przykładowy kod generuje C4290:

```
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```