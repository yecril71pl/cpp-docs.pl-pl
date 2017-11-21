---
title: "C2807 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2807
dev_langs: C++
helpviewer_keywords: C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5fbea2518dabf2851ff6d620095c898f7a2a35c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2807"></a>C2807 błąd kompilatora
drugi formalny parametr dla przyrostkowego "operator operator" musi być "int"  
  
 Drugi parametr operatora przyrostkowego ma zły typ.  
  
 Poniższy przykład generuje C2807:  
  
```  
// C2807.cpp  
// compile with: /c  
class X {  
public:  
   X operator++ ( X );   // C2807 nonvoid parameter  
   X operator++ ( int );   // OK, int parameter  
};  
```