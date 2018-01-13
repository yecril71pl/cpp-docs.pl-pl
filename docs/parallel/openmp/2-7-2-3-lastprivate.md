---
title: 2.7.2.3 lastprivate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5caf9d870dce301c6055dcb55418b3dbbc3e741f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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