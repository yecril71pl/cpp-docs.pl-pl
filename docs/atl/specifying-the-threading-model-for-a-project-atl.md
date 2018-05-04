---
title: Określanie modelu wątkowości projektu (ALT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f807aa82a62fb703430ace5bc6be516e08ca9dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Określanie modelu wątkowości projektu (ALT)
Następujące makra są dostępne do określania modelu wątkowości projektu ATL:  
  
|Macro|Wskazówki dotyczące używania|  
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

