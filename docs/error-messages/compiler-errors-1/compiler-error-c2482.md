---
title: Błąd kompilatora C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 481920fa2d8c32bc872e7b8805188cc674e6fe28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564817"
---
# <a name="compiler-error-c2482"></a>Błąd kompilatora C2482

>"*identyfikator*": dynamiczna inicjalizacja danych "thread" nie jest dozwolone w kodzie zarządzany WinRT

## <a name="remarks"></a>Uwagi

W zarządzanych lub kod WinRT, zmienne zadeklarowane za pomocą [__declspec(thread)](../../cpp/thread.md) atrybutu modyfikator klasy magazynu lub [thread_local](../../cpp/storage-classes-cpp.md#thread_local) specyfikatora klasy magazynu nie można zainicjować za pomocą wyrażenia wymaga wersji ewaluacyjnej, w czasie wykonywania. Statyczne wyrażenie jest wymagane do zainicjowania `__declspec(thread)` lub `thread_local` danych w tych środowiskach środowiska uruchomieniowego.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2482 w zarządzanych (**/CLR**) i WinRT (**/ZW**) kod:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Aby rozwiązać ten problem, inicjowanie magazynu wątków lokalnych za pomocą stałą, **constexpr**, lub wyrażenie statyczne. Wykonać oddzielnie inicjowanie właściwe dla wątków.