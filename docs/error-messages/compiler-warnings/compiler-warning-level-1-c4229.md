---
title: Kompilatora (poziom 1) ostrzeżenie C4229 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4229
dev_langs:
- C++
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c902bf397d5906645a9310da337561627d7c443
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4229"></a>Kompilator C4229 ostrzegawcze (poziom 1)
użyto konstrukcji przestarzałej: Modyfikatory dla danych są ignorowane.  
  
 Przy użyciu modyfikatora firmy Microsoft, takich jak `__cdecl` danych w deklaracji jest przestarzała metoda.  
  
## <a name="example"></a>Przykład  
  
```  
// C4229.cpp  
// compile with: /W1 /LD  
int __cdecl counter;   // C4229 cdecl ignored  
```