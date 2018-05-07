---
title: Kompilatora (poziom 1) ostrzeżenie C4399 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b39f4919dd736e4bf2e6230fe68ea69c2b14766e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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