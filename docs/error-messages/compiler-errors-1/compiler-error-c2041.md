---
title: "C2041 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2041
dev_langs: C++
helpviewer_keywords: C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4102f95b5a48860cba2e9ec79d2d5c22cd1413cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2041"></a>C2041 błąd kompilatora
Niedozwolony cyfrę "character" podstawowego numeru  
  
 Określony znak nie jest prawidłową cyfrą dla podstawy (na przykład ósemkowe i szesnastkowe).  
  
 Poniższy przykład generuje C2041:  
  
```  
// C2041.cpp  
int i = 081;   // C2041  8 is not a base 8 digit  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2041b.cpp  
// compile with: /c  
int j = 071;  
```