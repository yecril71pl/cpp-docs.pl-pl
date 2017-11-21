---
title: "2.4.2 — konstrukcja sekcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 22aa4cc1bde59234d70803c2e878d3fbf83f499e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="242-sections-construct"></a>2.4.2 — konstrukcja sekcji
**Sekcje** dyrektywy identyfikuje noniterative konstrukcji podziału pracy, który określa zbiór konstrukcje, które mają być podzielony między wątków w zespole. Każda sekcja jest wykonywana raz przez wątek w zespole. Składnia **sekcje** dyrektywy wygląda następująco:  
  
```  
#pragma omp sections [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block ]  
...  
}  
```  
  
 Klauzuli jest jednym z następujących czynności:  
  
 **prywatne (** *zmiennej listy* **)**  
  
 **firstprivate (** *zmiennej listy* **)**  
  
 **lastprivate (** *zmiennej listy* **)**  
  
 **redukcja (** *operator* **:***zmiennej listy* **)**   
  
 **NOWAIT**  
  
 Każda sekcja jest poprzedzony **sekcji** dyrektywy, mimo że **sekcji** dyrektywa jest opcjonalne w pierwszej sekcji. **Sekcji** dyrektywy musi występować w ramach zakresu leksykalne **sekcje** dyrektywy. Na koniec istnieje niejawna bariery **sekcje** skonstruować, chyba że **nowait** jest określona.  
  
 Ograniczenia **sekcje** dyrektywy są następujące:  
  
-   A **sekcji** dyrektywa nie musi występować poza zakres leksykalne **sekcje** dyrektywy.  
  
-   Tylko jeden **nowait** klauzula może występować w **sekcje** dyrektywy.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **prywatne**, **firstprivate**, **lastprivate**, i **redukcji** klauzule, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.