---
title: "Instrukcja o wartości null | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ecaa8d968efa9a3cd8c700d3d4dfe4cae0f0dd53
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="null-statement"></a>Instrukcja o wartości Null
"Instrukcja o wartości null" jest instrukcja wyrażenia z *wyrażenie* Brak. Jest przydatne w przypadku składni języka odwołuje się do instrukcji, ale nie Obliczanie wyrażenia. Składa się z średnikiem.  
  
 Instrukcje null są często używane jako symbole zastępcze w instrukcji iteracji lub instrukcji, w której ma zostać umieszczony etykiet na końcu instrukcje złożone lub funkcji.  
  
 Poniższy fragment kodu przedstawia sposób kopiowania jednego ciągu na inny i dołącza instrukcja o wartości null:  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja wyrażeń](../cpp/expression-statement.md)