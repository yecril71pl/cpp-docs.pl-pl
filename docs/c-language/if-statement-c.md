---
title: Jeśli Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else
- if
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f307860ce71e8c9fc74b2ab97e88ced02e08332f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387053"
---
# <a name="if-statement-c"></a>if — instrukcja (C)
**Jeśli** instrukcji steruje rozgałęzień warunkowych. Treść **Jeśli** instrukcja jest wykonywana, jeśli wartość wyrażenia jest różna od zera. Składnia **Jeśli** instrukcji ma dwie formy.  
  
## <a name="syntax"></a>Składnia  
 *Wybór instrukcji*:  
 **Jeśli (***wyrażenie***)***— instrukcja*  
  
 **Jeśli (***wyrażenie***)***instrukcji***else***— instrukcja*  
  
 W obu formach **Jeśli** instrukcji, wyrażeń, które mogą mieć dowolną wartość z wyjątkiem strukturą, są oceniane, w tym wszystkie efekty uboczne.  
  
 W formularzu pierwszy składni Jeśli *wyrażenie* ma wartość true (różną od zera), *instrukcji* jest wykonywana. Jeśli *wyrażenie* ma wartość false, *instrukcji* jest ignorowana. W drugiej formy składni, który używa **else**, drugi *instrukcji* jest wykonywana w przypadku *wyrażenie* ma wartość false. Za pomocą obu formularze kontrolować następnie przekazuje z **Jeśli** instrukcji do następnej instrukcji w programie dopóki zawiera jedno z oświadczeń **podziału**, **kontynuować**, lub `goto`.  
  
 Poniżej przedstawiono przykłady **Jeśli** instrukcji:  
  
```  
if ( i > 0 )  
    y = x / i;  
else   
{  
    x = i;  
    y = f( x );  
}  
```  
  
 W tym przykładzie instrukcja `y = x/i;` jest wykonywana w przypadku `i` jest większa niż 0. Jeśli `i` jest mniejsza niż lub równa 0, `i` jest przypisany do `x` i `f( x )` jest przypisany do `y`. Należy pamiętać, że instrukcja tworzące **Jeśli** klauzuli kończy się średnikiem.  
  
 Podczas zagnieżdżania **Jeśli** instrukcje i **else** klauzule, Użyj nawiasów klamrowych do instrukcji i klauzule w złożonej instrukcji, które Sprecyzuj wyrażenie użytkownika. Jeśli istnieją nie nawiasów klamrowych, kompilator usuwa niejednoznaczności kojarząc każdego **else** z najbardziej **Jeśli** bez **else**.  
  
```  
if ( i > 0 )           /* Without braces */  
    if ( j > i )  
        x = j;  
    else  
        x = i;  
```  
  
 **Else** klauzuli jest skojarzony z wewnętrznych **Jeśli** instrukcji w tym przykładzie. Jeśli `i` jest mniejsza lub równa 0, nie przypisano żadnej wartości do `x`.  
  
```  
if ( i > 0 )   
{                      /* With braces */  
    if ( j > i )  
        x = j;  
}  
else  
    x = i;  
```  
  
 Nawiasy otaczające wewnętrzny **Jeśli** instrukcji w tym przykładzie należy **else** klauzuli część zewnętrznego **Jeśli** instrukcji. Jeśli `i` jest mniejsza niż lub równa 0, `i` jest przypisany do `x`.  
  
## <a name="see-also"></a>Zobacz też  
 [if-else, instrukcja (C++)](../cpp/if-else-statement-cpp.md)