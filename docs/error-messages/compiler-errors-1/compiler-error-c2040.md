---
title: "C2040 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2040
dev_langs: C++
helpviewer_keywords: C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3504c8e18637ef907d5ab9c941ef7ad550daedf0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2040"></a>C2040 błąd kompilatora
"operator": "identifier1" różni się w poziomach pośredników od "identifier2"  
  
 Wyrażenie dotyczące określonego argumenty operacji typów niezgodne operand lub niejawnie przekonwertować typu argumentu operacji. Jeśli oba argumenty są arytmetyczne, lub obie nonarithmetic (na przykład tablicy lub wskaźnika), są one używane bez zmian. Jeśli jeden operand jest arytmetyczne, a drugi nie, arytmetyczny operand jest konwertowana na typ argumentu nonarithmetic.  
  
 W tym przykładzie generuje C2040 i pokazuje, jak go naprawić.  
  
```  
// C2040.cpp  
// Compile by using: cl /c /W3 C2040.cpp  
bool test() {  
   char c = '3';  
   return c == "3"; // C2446, C2040  
   // return c == '3'; // OK  
}  
```