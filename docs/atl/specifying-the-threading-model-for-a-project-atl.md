---
title: Określanie modelu wątkowości projektu (ALT)
ms.date: 11/04/2016
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
ms.openlocfilehash: 419c9880573c2058b3bb60b9c77e4f3ca065fab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569887"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Określanie modelu wątkowości projektu (ALT)

Następujące makra są dostępne do określania modelu wątkowości projektu ATL:

|Macro|Wskazówki dotyczące używania|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|Określenie, czy wszystkie obiekty używać pojedynczego modelu wątkowości.|
|_ATL_APARTMENT_THREADED|Zdefiniuj użycie co najmniej jeden z obiektów wątkowości typu apartment.|
|_ATL_FREE_THREADED|Zdefiniuj użycie co najmniej jeden z obiektów bezpłatnej lub neutralnym wątków. Istniejący kod może zawierać odwołania do równoważne — makro [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded).|

Jeśli nie zdefiniowano żadnego z tych makr w projekcie, _ATL_FREE_THREADED będą obowiązywać.

Makra wpłynąć na wydajność środowiska wykonawczego w następujący sposób:

- Określanie makro, które odnosi się do obiektów w projekcie może poprawić wydajność środowiska wykonawczego.

- Określanie wyższego poziomu makra, na przykład jeśli określisz _ATL_APARTMENT_THREADED, gdy wszystkie obiekty są pojedynczego wątku, nieco spowoduje zmniejszenie wydajności w czasie wykonywania.

- Określenie niższego poziomu makra, na przykład, jeśli określisz _ATL_SINGLE_THREADED, gdy dla jednego lub więcej obiektów wątkowość lub wolnych wątków może spowodować awarię w czasie wykonywania aplikacji.

Zobacz [opcji, Kreator obiektów proste ATL](../atl/reference/options-atl-simple-object-wizard.md) opis wątkowości modele dostępne dla obiektu ATL.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)

