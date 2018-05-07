---
title: Kompilatora (poziom 1) ostrzeżenie C4470 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4470
dev_langs:
- C++
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57fa405f1137c8627b439110514f63fd3e62d83b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4470"></a>Kompilator C4470 ostrzegawcze (poziom 1)
Formant zmiennoprzecinkowych pragm zignorowane z opcją/CLR  
  
 Formant liczb zmiennoprzecinkowych pragm:  
  
-   [fenv_access](../../preprocessor/fenv-access.md)  
  
-   [float_control](../../preprocessor/float-control.md)  
  
-   [fp_contract](../../preprocessor/fp-contract.md)  
  
 nie obowiązują w obszarze [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Poniższy przykład generuje C4470:  
  
```  
// C4470.cpp  
// compile with: /clr /W1 /LD  
#pragma float_control(except, on)   // C4470  
```