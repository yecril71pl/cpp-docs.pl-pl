---
title: Kompilatora (poziom 1) ostrzeżenie C4293 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4293
dev_langs:
- C++
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad588b69db1a0b46efa708b472bfc2218d17c0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277130"
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