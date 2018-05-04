---
title: Instrukcja o wartości null | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 624ff1051977804e6cefd97a813dce36cacdc3e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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