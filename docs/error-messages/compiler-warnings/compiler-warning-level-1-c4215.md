---
title: "Kompilatora (poziom 1) ostrzeżenie C4215 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4215
dev_langs:
- C++
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 900b27141f6e74760dd80f76ebf4e12c1368603f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4215"></a>Kompilator C4215 ostrzegawcze (poziom 1)
użyto niestandardowego rozszerzenia: long float  
  
 Traktuj domyślne rozszerzenia Microsoft (/Ze) **long float** jako **podwójne**. Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) nie obsługuje. Użyj **podwójne** Aby zachować zgodność.  
  
 Poniższy przykład generuje C4215:  
  
```  
// C4215.cpp  
// compile with: /W1 /LD  
long float a;   // C4215  
  
// use the line below to resolve the warning  
// double a;  
```