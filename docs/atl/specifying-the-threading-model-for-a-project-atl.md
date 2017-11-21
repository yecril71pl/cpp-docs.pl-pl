---
title: "Określanie modelu wątkowości projektu (ALT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78d126564a736eafed2b51c0216b458844d4567a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Określanie modelu wątkowości projektu (ALT)
Następujące makra są dostępne do określania modelu wątkowości projektu ATL:  
  
|Makra|Wskazówki dotyczące używania|  
|-----------|--------------------------|  
|_ATL_SINGLE_THREADED —|Określenie, czy wszystkie obiekty używać pojedynczego modelu wątkowości.|  
|_ATL_APARTMENT_THREADED —|Zdefiniuj użycie co najmniej jeden z obiektów wątkowości typu apartment.|  
|_ATL_FREE_THREADED —|Zdefiniuj użycie co najmniej jeden z obiektów wolnego lub neutralną wątków. Istniejący kod może zawierać odwołania do równoważne makro [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded).|  
  
 Jeśli nie zdefiniować dowolną z tych makr w projekcie, _atl_free_threaded — będzie obowiązywać.  
  
 Makra wpłynąć na wydajność środowiska wykonawczego w następujący sposób:  
  
-   Określanie makra, umożliwiająca obiektów w projekcie może poprawić wydajność środowiska wykonawczego.  
  
-   Określanie wyższym poziomie makra, na przykład jeśli określisz _atl_apartment_threaded — w przypadku wszystkich obiektów pojedynczego wątku, nieco spowoduje zmniejszenie wydajności w czasie wykonywania.  
  
-   Określenie niższego poziomu makra, na przykład określić _atl_single_threaded — gdy dla jednego lub więcej obiektów za pomocą wątkowości typu apartment lub wolnych wątków można spowodować, że aplikacja się niepowodzeniem w czasie wykonywania.  
  
 Zobacz [opcji, Kreator prostych obiektów ATL](../atl/reference/options-atl-simple-object-wizard.md) opis wątkowość modele dostępne dla obiekt ATL.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

