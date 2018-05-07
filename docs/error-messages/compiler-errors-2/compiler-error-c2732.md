---
title: C2732 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2faf21eb6f0c73d02ea32c7d4ed53f86eec3de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2732"></a>C2732 błąd kompilatora
Specyfikacja powiązania jest sprzeczna z wcześniejszą specyfikacją dla "function"  
  
 Funkcja jest już zadeklarowany ze specyfikatorem innego połączenia.  
  
 Ten błąd może być spowodowany przez zawierają pliki z specyfikatory różnych połączenie.  
  
 Aby naprawić ten błąd, należy zmienić `extern` instrukcje, aby zaakceptować powiązań. W szczególności nie jest zawijany `#include` dyrektywy w `extern "C"` bloków.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2732:  
  
```  
// C2732.cpp  
extern void func( void );   // implicit C++ linkage  
extern "C" void func( void );   // C2732  
```