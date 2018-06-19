---
title: Kompilatora (poziom 1) ostrzeżenie C4215 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4215
dev_langs:
- C++
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d5e07b9382c24f82f3e7d84fe82aee9dd91ca19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277608"
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