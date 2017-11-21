---
title: "C3893 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3893
dev_langs: C++
helpviewer_keywords: C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 49097d988175e7571c5825b4d54e1dd496fb2ba7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3893"></a>C3893 błąd kompilatora
"var": wykorzystanie wartości l elementu członkowskiego danych initonly jest dozwolone tylko w konstruktorze wystąpienia klasy "type_name"  
  
 Statyczne [initonly](../../dotnet/initonly-cpp-cli.md) elementy członkowskie danych może mieć tylko w konstruktorze statycznym adresu.  
  
 Elementy członkowskie danych initonly (niestatyczna) wystąpienia może zawierać tylko adresu pobranego w konstruktorach wystąpień (niestatyczna).  
  
 Poniższy przykład generuje C3893:  
  
```  
// C3893.cpp  
// compile with: /clr  
ref struct Y1 {  
   Y1() : data_var(0) {  
      int% i = data_var;   // OK  
   }  
   initonly int data_var;  
};  
  
int main(){  
   Y1^ y= gcnew Y1;  
   int% i = y->data_var;   // C3893  
}  
```