---
title: "Kompilatora (poziom 1) ostrzeżenie C4293 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4293
dev_langs:
- C++
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba42fc37d03dd872028a3fb487bc9ae72a5f2c59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4293"></a>Kompilator C4293 ostrzegawcze (poziom 1)
"operator": licznik przesunięć ujemny lub zbyt duży, niezdefiniowane zachowanie  
  
 Jeśli licznik przesunięć jest ujemny lub zbyt duży, zachowanie obraz wynikowy jest niezdefiniowany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4293:  
  
```  
// C4293.cpp  
// compile with: /c /W1  
unsigned __int64 combine (unsigned lo, unsigned hi) {  
  
   return (hi << 32) | lo;   // C4293  
  
   // try the following line instead  
   // return ( (unsigned __int64)hi << 32) | lo;  
}  
```