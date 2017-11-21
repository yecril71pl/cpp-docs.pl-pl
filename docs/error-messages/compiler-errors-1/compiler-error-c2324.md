---
title: "C2324 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2324
dev_langs: C++
helpviewer_keywords: C2324
ms.assetid: 215f0544-85b0-452d-825f-17a388b6a61c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 34ce2658607f673806d93579bc6d47a59d5206cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2324"></a>C2324 błąd kompilatora
'Identyfikator': nieoczekiwany po prawej "name"  
  
 Destruktora jest wywoływana przy użyciu identyfikatora niepoprawne.  
  
 Poniższy przykład generuje C2324:  
  
```  
// C2324.cpp  
class A {};  
typedef A* pA_t;  
int i;  
  
int main() {  
   pA_t * ppa = new pA_t;  
   ppa->~i;   // C2324  
   ppa->~pA_t();   // OK  
}  
```