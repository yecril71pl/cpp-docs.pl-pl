---
title: Określanie modelu wątkowości projektu (ATL) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f8a37a3ec730b727f6e214aafad1a4acc65b1dc3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760032"
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

