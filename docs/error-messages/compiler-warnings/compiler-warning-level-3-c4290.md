---
title: Ostrzeżenie kompilatora (poziom 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5970aa439a450bda4c1a2036da299d5c3cfbdb7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198903"
---
# <a name="compiler-warning-level-3-c4290"></a>Ostrzeżenie kompilatora (poziom 3) C4290

C++Zignorowano specyfikację wyjątku z wyjątkiem wskazania, że funkcja nie jest __declspec (nothrow)

Funkcja jest zadeklarowana przy użyciu specyfikacji wyjątku, którą C++ element wizualny akceptuje, ale nie implementuje. Kod ze specyfikacjami wyjątków, które są ignorowane podczas kompilowania, może być konieczne ponowne skompilowanie i połączenie z użyciem ich ponownie w przyszłych wersjach obsługujących specyfikacje wyjątków.

Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Można uniknąć tego ostrzeżenia przy użyciu dyrektywy pragma [ostrzeżenia](../../preprocessor/warning.md) :

```cpp
#pragma warning( disable : 4290 )
```

Następujący przykładowy kod generuje C4290:

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
