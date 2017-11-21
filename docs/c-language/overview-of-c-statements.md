---
title: "Przegląd instrukcji C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc4f9bc1b34ed884548a2614444c75efd2277287
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-c-statements"></a>Przegląd instrukcji C
Instrukcje C składają się z tokenów, wyrażenia i inne instrukcje. Instrukcja, która stanowi część innej instrukcji jest nazywany "treść" otaczającej instrukcji. Każdy typ instrukcji podanych w następującej składni została szczegółowo opisana w tej sekcji.  
  
## <a name="syntax"></a>Składnia  
 *Instrukcja*:  
 [z etykietą instrukcji](../c-language/goto-and-labeled-statements-c.md)  
  
 [złożone — instrukcja](../c-language/compound-statement-c.md)  
  
 [Instrukcja wyrażeń](../c-language/expression-statement-c.md)  
  
 [Wybór — instrukcja](../c-language/if-statement-c.md)  
  
 [instrukcji iteracji](../c-language/do-while-statement-c.md)  
  
 [skok — instrukcja](../c-language/break-statement-c.md)  
  
 [Spróbuj except — instrukcja](../c-language/try-except-statement-c.md)  
  
 / * Specific Microsoft \* / [try-finally — instrukcji](../c-language/try-finally-statement-c.md)  / \* Specific firmy Microsoft\*/  
  
 Często treść instrukcji jest "złożone wyrażenie". Instrukcja złożona składa się z innych instrukcji, które mogą zawierać słów kluczowych. Instrukcja złożona rozdzielana klamrowym (**{}**). Wszystkie instrukcje C kończyć się średnikiem (**;**). Średnik jest terminatora instrukcji.  
  
 Instrukcja wyrażeń zawiera wyrażenie C, które mogą zawierać arytmetyczną lub operatorów logicznych wprowadzone w [wyrażenia i przydziały](../c-language/expressions-and-assignments.md). Instrukcja o wartości null jest pustą instrukcję.  
  
 Każda instrukcja C może się rozpoczynać etykietę identyfikującą składające się z nazwy i dwukropka. Ponieważ tylko `goto` instrukcji rozpoznaje etykiety instrukcji, etykiet instrukcji omówiono z `goto`. Zobacz [goto i Labeled — instrukcje](../c-language/goto-and-labeled-statements-c.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../c-language/statements-c.md)