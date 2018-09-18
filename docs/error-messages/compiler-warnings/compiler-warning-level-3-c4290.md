---
title: Kompilator ostrzeżenie (poziom 3) C4290 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a6f09d8f3396381f34a0fbe3c7150b5948cee01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46015977"
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