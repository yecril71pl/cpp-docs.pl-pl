---
title: C2382 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2382
dev_langs:
- C++
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a17a1038e7e5923e0ee7570754d5c146b55a06f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226225"
---
# <a name="compiler-error-c2382"></a>C2382 błąd kompilatora
"Funkcja": zmiana definicji; różne specyfikacje wyjątków  
  
 W obszarze [/Za](../../build/reference/za-ze-disable-language-extensions.md), ten błąd wskazuje przeciążenie funkcji podjęto tylko na [specyfikacji wyjątku](../../cpp/exception-specifications-throw-cpp.md).  
  
 Poniższy przykład generuje C2382:  
  
```  
// C2382.cpp  
// compile with: /Za /c  
void f1(void) throw(int) {}  
void f1(void) throw(char) {}   // C2382  
void f2(void) throw(char) {}   // OK  
```