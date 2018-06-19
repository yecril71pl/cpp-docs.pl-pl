---
title: C2768 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee0fd3fa213639e70199cfe5653ee2034bc39b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233386"
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