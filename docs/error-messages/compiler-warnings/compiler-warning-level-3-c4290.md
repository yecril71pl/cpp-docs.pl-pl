---
title: Kompilatora (poziom 3) ostrzeżenie C4290 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f03d35e1a3756979d8936647255e2b65afef56d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289896"
---
# <a name="compiler-warning-level-3-c4290"></a>Kompilator C4290 ostrzegawcze (poziom 3)
Specyfikację wyjątku C++ ignorowane, z wyjątkiem sygnalizacji, że funkcja nie jest __declspec(nothrow)  
  
 Funkcja jest zadeklarowana przy użyciu specyfikacji wyjątku, który akceptuje Visual C++, ale nie implementuje. Kodu z wyjątkiem potrzebnych specyfikacje, które są ignorowane, podczas kompilacji może być ponownie kompilowane i połączone za ponownie w przyszłych wersjach Obsługa specyfikacje wyjątków.  
  
 Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md) .  
  
 To ostrzeżenie można uniknąć, używając [ostrzeżenie](../../preprocessor/warning.md) pragma:  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 Poniższy przykład kodu generuje C4290:  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```