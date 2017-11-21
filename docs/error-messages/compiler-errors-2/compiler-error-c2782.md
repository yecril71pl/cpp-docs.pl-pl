---
title: "C2782 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2782
dev_langs: C++
helpviewer_keywords: C2782
ms.assetid: 8b685422-294d-4f64-9f3d-c14eaf03a93d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 125092771675363eb896d3524b8e093493f9719b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2782"></a>C2782 błąd kompilatora
"deklaracją": parametr szablonu 'Identyfikator' jest niejednoznaczny  
  
 Kompilator nie może określić typ argumentu szablonu.  
  
 Poniższy przykład generuje C2782:  
  
```  
// C2782.cpp  
template<typename T>  
void f(T, T) {}  
  
int main() {  
   f(1, 'c');   // C2782  
   // try the following line instead  
   // f<int>(1, 'c');  
}  
```  
  
 C2782 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2782b.cpp  
// compile with: /clr  
generic<typename T> void gf(T, T) { }  
  
int main() {  
   gf(1, 'c'); // C2782  
   // try the following line instead  
   // gf<int>(1, 'c');  
}  
```