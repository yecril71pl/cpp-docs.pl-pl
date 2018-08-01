---
title: Wartość null, poufności informacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab391bb75dd6e7a2ef1ccf0951fa93770e6cd316
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408522"
---
# <a name="null-statement"></a>Instrukcja o wartości Null
"Instrukcja o wartości null" jest za pomocą instrukcji wyrażenia *wyrażenie* Brak. Jest to przydatne, gdy składni języka wywołuje dla instrukcji, ale nie Obliczanie wyrażenia. Składa się z średnikiem.  
  
 Instrukcji o wartości null są często używane jako symbole zastępcze w wywołaniach iteracja — instrukcje lub instrukcji, na którym ma zostać umieszczony etykiet na końcu instrukcji złożonej lub funkcji.  
  
 Poniższy fragment kodu pokazuje, jak skopiować jednego ciągu do innego i dołącza instrukcja o wartości null:  
  
```cpp 
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcja wyrażeń](../cpp/expression-statement.md)