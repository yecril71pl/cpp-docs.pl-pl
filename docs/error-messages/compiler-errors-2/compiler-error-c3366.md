---
title: C3366 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c26bfbb5d66ad22484184bd361f14004ed8aa30c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3366"></a>C3366 błąd kompilatora
"Zmienna": statyczne elementy członkowskie danych zarządzane lub WinRTtypes musi być zdefiniowana w ramach definicji klasy  
  
 Próbowano odwołać statyczny element członkowski klasy WinRT lub .NET lub interfejs poza definicją klasy lub interfejsu.  
  
 Kompilator wymaga znajomości pełnej definicji klasy (aby emitować meta dane po jednym przebiegu) oraz statyczne elementy członkowskie danych do zainicjowania należące do klasy.  
  
 Na przykład poniższy przykład generuje C3366 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3366.cpp  
// compile with: /clr /c  
ref class X {  
   public:  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```  
