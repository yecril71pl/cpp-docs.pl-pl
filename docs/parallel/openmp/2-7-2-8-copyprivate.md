---
title: "2.7.2.8 — prywatna kopia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 21d739fb3ead0512776cfd996b59f1ceab5e8250
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="2728-copyprivate"></a>2.7.2.8 — prywatna kopia
**Copyprivate** klauzuli zapewnia mechanizm na potrzeby zmiennej prywatnej emisji wartość z jednego członka do zespołu do innych elementów członkowskich. Jest to alternatywa dla użycia udostępniona zmienna wartości, gdy dostarczanie udostępniona zmienna jest trudna (na przykład w rekursją wymagające innej zmiennej na każdym poziomie). **Copyprivate** klauzula może występować tylko w **pojedynczego** dyrektywy.  
  
 Składnia **copyprivate** klauzuli wygląda następująco:  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 Efekt **copyprivate** klauzuli na zmienne na swojej liście zmiennych występuje po wykonaniu strukturalnego bloku skojarzone z **pojedynczego** konstruowania i przed każdą wątków w zespół pozostać bariery na końcu konstrukcji. Następnie w innych wątków w zespole, dla każdej zmiennej w *zmiennej listy*, tej zmiennej staje się wynika z (tak, jakby przypisanie) z wartością odpowiadającego zmiennej w wątku, który konstrukcja wykonane przez strukturę blok.  
  
 Ograniczenia **copyprivate** klauzuli są następujące:  
  
-   Zmienna, która została określona w **copyprivate** klauzula nie musi występować w **prywatnej** lub **firstprivate** klauzulę dla tego samego **jednym**dyrektywy.  
  
-   Jeśli **pojedynczego** dyrektywy z **copyprivate** klauzuli napotkano dynamicznego zakresu równoległego regionu, wszystkie zmienne określone w **copyprivate** klauzuli musi być prywatny w otaczającym kontekście.  
  
-   Zmienna, która została określona w **copyprivate** klauzuli musi mieć operatora przypisania kopiowania jednoznaczne dostępny.