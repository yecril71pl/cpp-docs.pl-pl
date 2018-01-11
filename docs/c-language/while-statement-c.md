---
title: Podczas Statement (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: while
dev_langs: C++
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69f4dfa2feb48bf0fb8ea6f8fca90107c788137e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="while-statement-c"></a>while — instrukcja (C)
`while` Instrukcji umożliwia Powtórz instrukcję określone wyrażenie staje się wartość false.  
  
## <a name="syntax"></a>Składnia  
 *instrukcji iteracji*:  
 **gdy (***wyrażenie***)***— instrukcja*   
  
 *Wyrażenie* musi mieć typ arytmetyczny lub wskaźnikowy. Wykonanie przebiega w następujący sposób:  
  
1.  *Wyrażenie* oceny.  
  
2.  Jeśli *wyrażenie* początkowo wartość false, treść `while` instrukcji nie został wykonany i przekazuje kontroli z `while` instrukcji do następnej instrukcji w programie.  
  
     Jeśli *wyrażenie* jest true (różną od zera), treść instrukcji jest wykonywana, a proces jest powtarzany, poczynając od kroku 1.  
  
 `while` Instrukcji można również zakończyć kiedy **podziału**, `goto`, lub `return` w instrukcji treści jest wykonywana. Użyj **kontynuować** oświadczenie zakończenie iteracji bez zamykania `while` pętli. **Kontynuować** instrukcja przekazuje formantu do następnej iteracji `while` instrukcji.  
  
 To jest przykład `while` instrukcji:  
  
```  
while ( i >= 0 )   
{  
    string1[i] = string2[i];  
    i--;  
}  
```  
  
 Ten przykładowy kod kopiuje znaków z `string2` do `string1`. Jeśli `i` jest większa niż lub równa 0, `string2[i]` jest przypisany do `string1[i]` i `i` zostanie zmniejszona. Gdy `i` osiągnie lub spadnie poniżej 0, wykonywanie `while` kończy instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [while, instrukcja (C++)](../cpp/while-statement-cpp.md)