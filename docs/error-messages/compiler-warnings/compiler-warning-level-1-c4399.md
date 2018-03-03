---
title: "Kompilatora (poziom 1) ostrzeżenie C4399 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eff01c29d423b0823b41bf63702cf42ee839a523
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4399"></a>Kompilator C4399 ostrzegawcze (poziom 1)
"symbol": symbol w procesie nie powinien być oznaczony przez __declspec(dllimport), gdy skompilowano z opcją/CLR: pure  
  
 **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015.  
  
 Nie można zaimportować danych z obrazu macierzystego lub obrazu macierzystego i konstrukcje CLR w czysty obraz. Aby usunąć to ostrzeżenie, kompilacji z **/CLR** (nie **/CLR: pure**) lub usunąć `__declspec(dllimport)`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4399.  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```