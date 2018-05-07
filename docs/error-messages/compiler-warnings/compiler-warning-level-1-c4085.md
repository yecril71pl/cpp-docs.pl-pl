---
title: Kompilatora (poziom 1) ostrzeżenie C4085 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4085
dev_langs:
- C++
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9b8f1cfdb1cb8cc699b71a08afc417d2d1bd87f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4085"></a>Kompilator C4085 ostrzegawcze (poziom 1)
Oczekiwano wartości parametru pragma "on" lub "off"  
  
 Pragma wymaga **na** lub **poza** parametru. Pragma została zignorowana.  
  
 Poniższy przykład generuje C4085:  
  
```  
// C4085.cpp  
// compile with: /W1 /LD  
#pragma optimize( "t", maybe )  // C4085  
```