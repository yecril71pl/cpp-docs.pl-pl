---
title: "C2483 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2483
dev_langs:
- C++
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f7f9f30724c02d44e054bf16ff1460370c30e06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2483"></a>C2483 błąd kompilatora

>"*identyfikator*": obiekt o Konstruktor ani destruktor nie można zadeklarować jako "wątku"

Ten komunikat o błędzie jest przestarzała w programie Visual Studio 2015 i nowszych wersjach. W poprzednich wersjach zadeklarować z `thread` atrybutu nie można zainicjować z konstruktora lub inne wyrażenie, które wymaga oceny czasu wykonywania. Statyczne wyrażenia jest wymagane do zainicjowania `thread` danych.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2483 w programie Visual Studio 2013 i wcześniejszych wersjach.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error  

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Zobacz też

[wątek](../../cpp/thread.md)