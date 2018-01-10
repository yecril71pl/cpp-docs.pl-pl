---
title: "C3366 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3366
dev_langs: C++
helpviewer_keywords: C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d94d3a18c02cfe81f6c3ee96635c9388f54308d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
