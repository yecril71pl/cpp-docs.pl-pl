---
title: "C3803 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3803
dev_langs: C++
helpviewer_keywords: C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aec9e416833894bcd4c4d430b293e0867f544757
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3803"></a>C3803 błąd kompilatora
"właściwość": właściwość ma typ, który jest niezgodny z jednym z jego akcesorów "akcesor"  
  
 Typ właściwości zdefiniowane z [właściwości](../../cpp/property-cpp.md) jest niezgodny z typem zwracanym dla jednej z jego funkcji dostępu.  
  
 Poniższy przykład generuje C3803:  
  
```  
// C3803.cpp  
struct A  
{  
   __declspec(property(get=GetIt)) int i;  
   char GetIt()  
   {  
      return 0;  
   }  
  
   /*  
   // try the following definition instead  
   int GetIt()  
   {  
      return 0;  
   }  
   */  
}; // C3803  
  
int main()  
{  
}  
```