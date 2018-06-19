---
title: C2482 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2482
dev_langs:
- C++
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3dd23069f389d0a02e10d26edb7ee4fd3c373cb
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256009"
---
# <a name="compiler-error-c2482"></a>C2482 błąd kompilatora

>"*identyfikator*": dynamiczna inicjalizacja danych "wątek" nie jest dozwolona w kod zarządzany WinRT

## <a name="remarks"></a>Uwagi

W zarządzanych lub kodem WinRT, zmiennych zadeklarowano za pomocą [__declspec(thread)](../../cpp/thread.md) atrybutu modyfikator klasy magazynu lub [element thread_local](../../cpp/storage-classes-cpp.md#thread_local) Specyfikator klasy magazynu nie można zainicjować za pomocą wyrażenia wymagające oceny w czasie wykonywania. Statyczne wyrażenia jest wymagane do zainicjowania `__declspec(thread)` lub `thread_local` dane w tych środowiskach środowiska wykonawczego.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2482 w zarządzanych (**/CLR**) i w WinRT (**/ZW**) kodu:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Aby rozwiązać ten problem, zainicjować magazynu wątków lokalnych przy użyciu stałej, **constexpr**, lub wyrażenie statycznych. Inicjowanie właściwe dla wątków należy przeprowadzić oddzielnie.