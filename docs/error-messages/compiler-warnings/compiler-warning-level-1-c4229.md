---
title: "Kompilatora (poziom 1) ostrzeżenie C4229 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4229
dev_langs: C++
helpviewer_keywords: C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02ae82e18223373a3ee82c07f43ea65f7a92ec76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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