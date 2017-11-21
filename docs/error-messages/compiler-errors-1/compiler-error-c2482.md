---
title: "C2482 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2482
dev_langs: C++
helpviewer_keywords: C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3106e9610bc1c58651bf7be5e58af44429bceb74
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
