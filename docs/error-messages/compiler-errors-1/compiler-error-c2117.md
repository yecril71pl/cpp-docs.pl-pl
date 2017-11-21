---
title: "C2117 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2117
dev_langs: C++
helpviewer_keywords: C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e326e7a7dde296439d1a9c24c1d042af63dc6f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2117"></a>C2117 błąd kompilatora
"identyfikator": przepełnienie granic tablicy  
  
 Tablica ma zbyt wiele inicjatorów:  
  
-   Inicjatory i elementy tablicy nie są zgodne w rozmiaru i liczby.  
  
-   Nie miejsca dla terminatorem null w ciągu.  
  
 Poniższy przykład generuje C2117:  
  
```  
// C2117.cpp  
int main() {  
   char abc[4] = "abcd";   // C2117  
   char def[4] = "abd";   // OK  
}  
```