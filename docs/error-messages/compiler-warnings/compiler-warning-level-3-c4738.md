---
title: "Kompilatora (poziom 3) ostrzeżenie C4738 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4738
dev_langs: C++
helpviewer_keywords: C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30f56b7963d8c6e98d4564ec90adee6bd3d29f9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4738"></a>Kompilator C4738 ostrzegawcze (poziom 3)
przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności  
  
 C4738 wyświetli ostrzeżenie, że wynik przypisania, cast; przekazany argument lub inna operacja może wymagać ma zostać zaokrąglona lub czy operacja zabrakło rejestrów i niezbędne do używania pamięci (przechodzeniu). Może to spowodować utratę wydajności.  
  
 Aby rozwiązać to ostrzeżenie i uniknąć zaokrąglania, kompilacji z [Fast](../../build/reference/fp-specify-floating-point-behavior.md) lub użyj `double` zamiast `float`.  
  
 Rozwiązanie to ostrzeżenie i uniknąć wyczerpaniu rejestrów, zmienić kolejność obliczeń i zmodyfikuj korzystanie z ze śródwierszowaniem  
  
 To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4738:  
  
```  
// C4738.cpp  
// compile with: /c /fp:precise /O2 /W3  
// processor: x86  
#include <stdio.h>  
  
#pragma warning(default : 4738)  
  
float func(float f)  
{  
    return f;  
}  
  
int main()  
{  
    extern float f, f1, f2;  
    double d = 0.0;  
  
    f1 = func(d);  
    f2 = (float) d;  
    f = f1 + f2;   // C4738  
    printf_s("%f\n", f);  
}  
```