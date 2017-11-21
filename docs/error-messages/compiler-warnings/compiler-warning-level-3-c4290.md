---
title: "Kompilatora (poziom 3) ostrzeżenie C4290 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4290
dev_langs: C++
helpviewer_keywords: C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ccf7fee7cafb771f669a4d8730fed7c6c323c3c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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