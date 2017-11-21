---
title: "Kompilatora (poziom 1) ostrzeżenie C4230 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4230
dev_langs: C++
helpviewer_keywords: C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0197e214a697be5a8e1ecd35eadeceb494669aff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4230"></a>Kompilator C4230 ostrzegawcze (poziom 1)
użyto konstrukcji przestarzałej: Modyfikatory/kwalifikatory przeplatane; Zignorowano kwalifikator  
  
 Przy użyciu kwalifikatora przed modyfikator firmy Microsoft, takich jak `__cdecl` jest przestarzała metoda.  
  
## <a name="example"></a>Przykład  
  
```  
// C4230.cpp  
// compile with: /W1 /LD  
int __cdecl const function1();   // C4230 const ignored  
```