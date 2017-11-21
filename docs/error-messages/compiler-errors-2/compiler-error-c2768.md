---
title: "C2768 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2768
dev_langs: C++
helpviewer_keywords: C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 79693c3d7b337302698d7854b5cd447ce7c68334
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2768"></a>C2768 błąd kompilatora
"Funkcja": niedozwolone użycie argumentów jawnego szablonu  
  
 Kompilator nie może określić, jeśli definicji funkcji powinna być jawna specjalizacja szablonu funkcji lub definicji funkcji został powinien być dla nowych funkcji.  
  
 Ten błąd został wprowadzony w Visual Studio .NET 2003 jako część rozszerzenia zgodność kompilatora.  
  
 Poniższy przykład generuje C2768:  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```