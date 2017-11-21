---
title: "C2283 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2283
dev_langs: C++
helpviewer_keywords: C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c6c3a02fcd88f5bb61e6856ad841883a17718d1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2283"></a>C2283 błąd kompilatora
"identyfikator": czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony dla nienazwanego — struktura  
  
 Funkcję elementu członkowskiego nienazwanej klasy lub struktury jest zadeklarowana ze specyfikatorem czystego, co jest niedozwolone.  
  
 Poniższy przykład generuje C2283:  
  
```  
// C2283.cpp  
// compile with: /c  
struct {  
   virtual void func() = 0;   // C2283  
};  
struct T {  
   virtual void func() = 0;   // OK  
};  
```