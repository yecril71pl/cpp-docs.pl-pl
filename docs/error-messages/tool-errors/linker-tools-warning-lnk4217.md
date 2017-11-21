---
title: "Ostrzeżenie LNK4217 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4217
dev_langs: C++
helpviewer_keywords: LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 35b82a1f5f21cdaad6dfd7d5d970a65e10e0b0a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4217"></a>Ostrzeżenie LNK4217 narzędzi konsolidatora
lokalnie zdefiniowany symbol "symbol" zaimportowany w funkcji "function"  
  
 [__declspec(DllImport)](../../cpp/dllexport-dllimport.md) została określona dla symbolu, nawet jeśli symbol jest zdefiniowany lokalnie. Usuń `__declspec` modyfikator rozwiązywać to ostrzeżenie.  
  
 `symbol`to nazwa symbolu, który jest zdefiniowany w obrazie. `function`to funkcja, która jest zaimportowanie symbolu.  
  
 To ostrzeżenie nie będą wyświetlane podczas kompilowania przy użyciu opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 LNK4217 może również wystąpić przy próbie Połącz dwa moduły, gdy zamiast tego należy skompilować drugiego modułu z biblioteką importu pierwszego modułu.  
  
```  
// LNK4217.cpp  
// compile with: /LD  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 a następnie  
  
```  
// LNK4217b.cpp  
// compile with: /c  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 Próba połączenia tych dwóch modułów powoduje LNK4217, skompilować drugiej próbki z biblioteką importu pierwszej próby rozwiązania.