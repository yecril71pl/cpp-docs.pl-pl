---
title: "2.9 zagnieżdżanie dyrektywy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd3c4f790681b1b044f435c03d185585b565eb62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="29-directive-nesting"></a>2.9 Zagnieżdżanie dyrektywy
Dynamiczne zagnieżdżanie dyrektywy muszą być zgodne z następującymi zasadami:  
  
-   A **równoległych** dyrektywy dynamicznie wewnątrz innego **równoległych** logicznie ustanawia nowy zespół, który składa się z bieżącego wątku, chyba że zagnieżdżone równoległości jest włączona.  
  
-   **dla**, **sekcje**, i **pojedynczego** dyrektywy, które wiążą się do tej samej **równoległych** nie mogą być zagnieżdżone wewnątrz siebie nawzajem.  
  
-   **krytyczne** dyrektywy o takiej samej nazwie nie mogą być zagnieżdżone wewnątrz siebie nawzajem. Należy zauważyć, że to ograniczenie nie są wystarczające do uniknięcia zakleszczenia.  
  
-   **dla**, **sekcje**, i **pojedynczego** dyrektywy nie są dozwolone w zakresie dynamiczne **krytyczne**, **uporządkowane**, i **wzorca** regionów, jeśli dyrektywy powiązania do tej samej **równoległych** jako regionów.  
  
-   **bariera** dyrektywy nie są dozwolone w zakresie dynamiczne **dla**, **uporządkowane**, **sekcje**, **pojedynczego**, **wzorca**, i **krytyczne** regionów, jeśli dyrektywy powiązania do tej samej **równoległych** jako regionów.  
  
-   **główny** dyrektywy nie są dozwolone w zakresie dynamiczne **dla**, **sekcje**, i **pojedynczego** dyrektywy Jeśli **wzorzec** dyrektywy powiązania do tej samej **równoległych** jako podziału pracy dyrektywy.  
  
-   **uporządkowane** dyrektywy nie są dozwolone w zakresie dynamiczne **krytyczne** regionów, jeśli dyrektywy powiązania do tej samej **równoległych** jako regionów.  
  
-   Wszystkie dyrektywy, które są dozwolone podczas wykonywania dynamicznie w ramach równoległego regionu również jest dozwolone, gdy wykonywane poza równoległego regionu. Po wykonaniu dynamicznie poza określonymi przez użytkownika równoległego regionu dyrektywa jest wykonywana przez zespół składa się z głównego wątku.