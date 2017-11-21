---
title: "C4430 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4430
dev_langs: C++
helpviewer_keywords: C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4455419ab6ce8a98dfb26bdb6575cc229d364c0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4430"></a>C4430 ostrzeżenia kompilatora
brak specyfikatora typu — zakładany int. Uwaga: C++ nie obsługuje domyślnie typu int  
  
 Ten błąd może być wygenerowanego w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: wszystkie deklaracje jawnie określić typ; jest już założono, że.  
  
 C4430 jest zawsze wystawione jako błąd.  Możesz wyłączyć to ostrzeżenie o `#pragma warning` lub **/wd**; zobacz [ostrzeżenie](../../preprocessor/warning.md) lub [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md)Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4430.  
  
```  
// C4430.cpp  
// compile with: /c  
struct CMyClass {  
   CUndeclared m_myClass;  // C4430  
   int m_myClass;  // OK  
};  
  
typedef struct {  
   POINT();   // C4430  
   // try the following line instead  
   // int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```