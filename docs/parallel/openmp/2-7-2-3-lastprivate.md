---
title: 2.7.2.3 lastprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08f331862d6e48b1c0882382285ddffa9699e79c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687345"
---
# <a name="2723-lastprivate"></a>2.7.2.3 ostatnia prywatna
`lastprivate` Klauzuli stanowi nadzbiór funkcje udostępniane przez `private` klauzuli. Składnia `lastprivate` klauzuli wygląda następująco:  
  
```  
lastprivate(variable-list)  
```  
  
 Zmienne określone w *zmiennej listy* ma `private` klauzuli semantyki. Gdy `lastprivate` klauzuli pojawia się w dyrektywie, który identyfikuje konstrukcji podziału pracy, wartość każdego `lastprivate` zmiennej sekwencyjnie ostatnich iteracji pętli skojarzone lub lexically ostatniego dyrektywą sekcji, jest przypisany do oryginalny obiekt w zmiennej. Zmienne, które nie są przypisane wartości przez ostatnich iteracji **dla** lub **równoległe w**, lub lexically ostatniej sekcji **sekcje** lub  **sekcji równoległych** dyrektywy mają wartości nieokreślony po konstrukcji. Nieprzypisane podobiektów również ma nieokreśloną wartość po konstrukcji.  
  
 Ograniczenia do `lastprivate` klauzuli są następujące:  
  
-   Wszystkie ograniczenia dla `private` zastosowania.  
  
-   Zmienna typu klasy jest określony jako `lastprivate` musi być dostępny, jednoznaczne kopia operatora przypisania.  
  
-   Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w `reduction` klauzuli **równoległych** dyrektywy nie można określić w `lastprivate` klauzuli w dyrektywie podziału pracy, która jest powiązana z konstrukcji równoległych.