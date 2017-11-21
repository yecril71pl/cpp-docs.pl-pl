---
title: "Kompilatora (poziom 3) ostrzeżenie C4159 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4159
dev_langs: C++
helpviewer_keywords: C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1997fc9b210723c5747f67e3b042987043c5c161
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4159"></a>Kompilator C4159 ostrzegawcze (poziom 3)
\#pragma pragma(pop,...): ma zdjęte ze stosu poprzednio włożony identyfikator "identyfikator"  
  
 Kod źródłowy zawiera **wypychania** następuje instrukcji z identyfikatorem pragma **pop** instrukcji bez identyfikatora. W związku z tym ***identyfikator*** jest zdjęte ze stosu, a kolejne zastosowań ***identyfikator*** może spowodować nieoczekiwane zachowanie.  
  
 Aby uniknąć tego ostrzeżenia, należy podać identyfikator w **pop** instrukcji. Na przykład:  
  
```  
// C4159.cpp  
// compile with: /W3  
#pragma pack(push, f)  
#pragma pack(pop)   // C4159  
  
// using the identifier resolves the warning  
// #pragma pack(pop, f)  
  
int main()  
{  
}  
```