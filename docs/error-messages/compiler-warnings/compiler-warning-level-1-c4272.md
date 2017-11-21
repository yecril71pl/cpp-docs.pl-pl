---
title: Kompilator ostrzegawcze (poziom 1) C4272 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4272
dev_langs: C++
helpviewer_keywords: C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8d5709ec229ea3e1bfbb985fa35937c7c26b7646
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4272"></a>Kompilator ostrzegawcze (poziom 1) C4272
"Funkcja": jest oznaczony jako __declspec(dllimport); należy określić natywną Konwencję wywoływania podczas importu funkcji.  
  
 Błąd, aby wyeksportować funkcji oznaczonych [__clrcall](../../cpp/clrcall.md) wywoływanie Konwencji i kompilator wystawia to ostrzeżenie, jeśli podjąć próbę zaimportowania funkcja oznaczona `__clrcall`.  
  
 Poniższy przykład generuje C4272:  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```