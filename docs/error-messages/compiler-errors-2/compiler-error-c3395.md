---
title: "C3395 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3395
dev_langs: C++
helpviewer_keywords: C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 93009d77c40535997ecc42ccb715f5fe81d79798
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3395"></a>C3395 błąd kompilatora
"Funkcja": nie można zastosować __declspec(dllexport) do funkcji z \__clrcall konwencji wywoływania  
  
 `__declspec(dllexport)`i [__clrcall](../../cpp/clrcall.md) nie są zgodne.  Aby uzyskać więcej informacji, zobacz [dllexport i dllimport](../../cpp/dllexport-dllimport.md).  
  
 Poniższy przykład generuje C3395:  
  
```  
// C3395.cpp  
// compile with: /clr /c  
  
__declspec(dllexport) void __clrcall Test(){}   // C3395  
void __clrcall Test2(){}   // OK  
__declspec(dllexport) void Test3(){}   // OK  
```