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
ms.openlocfilehash: f2c4725dd357854db504272e5b8b9d88641b143d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2482"></a>C2482 błąd kompilatora

>"*identyfikator*": dynamiczna inicjalizacja danych "wątek" nie jest dozwolone

Ten komunikat o błędzie jest przestarzała w programie Visual Studio 2015 i nowszych wersjach. W poprzednich wersjach zadeklarować przy użyciu `thread` atrybutu nie można zainicjować z wyrażeniem, które wymaga oceny czasu wykonywania. Statyczne wyrażenia jest wymagane do zainicjowania `thread` danych.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2482 w programie Visual Studio 2013 i starszych wersji:

```cpp
// C2482.cpp
// compile with: /c
#define Thread __declspec( thread )
Thread int tls_i = tls_i;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
```
