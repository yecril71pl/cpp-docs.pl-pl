---
title: "Kompilatora (poziom 4) ostrzeżenie C4668 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4668
dev_langs: C++
helpviewer_keywords: C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 059bf2dcb2d854ad05d21a9314d0d6a3f2a7a432
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4668"></a>Kompilator C4668 ostrzegawcze (poziom 4)
'symbol' nie jest zdefiniowany jako makro preprocesora, zastępowanie przez '0' dla 'dyrektywy'  
  
 Symbol, który nie został zdefiniowany została użyta z dyrektywy preprocesora. Symbol zwróci wartość false. Aby zdefiniować symbolu, możesz użyć dowolnej [#define — dyrektywa](../../preprocessor/hash-define-directive-c-cpp.md) lub [/D](../../build/reference/d-preprocessor-definitions.md) — opcja kompilatora.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4668:  
  
```  
// C4668.cpp  
// compile with: /W4  
#include <stdio.h>  
  
#pragma warning (default : 4668)   // turn warning on  
  
int main()   
{  
    #if q   // C4668, q is not defined  
        printf_s("defined");  
    #else  
        printf_s("undefined");  
    #endif  
}  
```