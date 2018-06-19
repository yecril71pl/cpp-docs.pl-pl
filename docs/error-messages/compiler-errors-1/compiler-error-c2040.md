---
title: C2040 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2040
dev_langs:
- C++
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b19a5dd647e51efb46ef9798b7f7cdff5339b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167544"
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