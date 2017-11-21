---
title: "Kompilatora (poziom 3) ostrzeżenie C4287 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4287
dev_langs: C++
helpviewer_keywords: C4287
ms.assetid: 1bf3bff8-6402-4d06-95ba-431678a790a7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4bf14de482bde86233ac543e889f89c55a49cf5d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4287"></a>Kompilator C4287 ostrzegawcze (poziom 3)
"operator": niezgodność stałej bez znaku ujemna  
  
 Niepodpisane zmiennej został użyty w operacji z liczbą ujemną.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4287:  
  
```  
// C4287.cpp  
// compile with: /W3  
#pragma warning(default : 4287)  
#include <stdio.h>  
  
int main()  
{  
    unsigned int u = 1;  
    if (u < -1)   // C4287  
        printf_s("u LT -1");  
    else  
        printf_s("u !LT -1");  
    return 0;  
}  
```