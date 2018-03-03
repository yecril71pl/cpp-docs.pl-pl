---
title: "Kompilatora (poziom 2) ostrzeżenie C4308 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4308
dev_langs:
- C++
helpviewer_keywords:
- C4308
ms.assetid: d4e5c53c-71b2-4bbc-8a7c-3a2a3180d9d9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb72f8df68917b9297a0e0e397ffcfddfccb910d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4308"></a>Kompilator C4308 ostrzegawcze (poziom 2)
ujemne stałe całkowite skonwertowano na typ bez znaku  
  
 Wyrażenie konwertuje stałą całkowitą ujemną typu bez znaku. Wynikiem wyrażenia jest prawdopodobnie znaczenia.  
  
## <a name="example"></a>Przykład  
  
```  
// C4308.cpp  
// compile with: /W2  
unsigned int u = (-5 + 3U);   // C4308  
  
int main()  
{  
}  
```