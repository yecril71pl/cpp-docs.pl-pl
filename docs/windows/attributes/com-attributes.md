---
title: Atrybuty COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 83d518aded30215684970e58d2868625fb8cd0e5
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789766"
---
# <a name="com-attributes"></a>Atrybuty COM

Atrybuty COM wstrzyknąć kod obsługujący wiele obszarów projektowania modelu COM i .NET Framework — programowanie środowiska uruchomieniowego języka wspólnego. Te obszary w zakresie od implementacji niestandardowego interfejsu i obsługa istniejące interfejsy do obsługi podstawowe właściwości, metody i zdarzenia. Ponadto pomocy technicznej można znaleźć złożone i implementacją kontrolki ActiveX.
  
|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że formant może być agregowany przez inny formant.|
|[aggregates](aggregates.md)|Wskazuje, że formant agreguje klasy docelowej.|
|[coclass](coclass.md)|Tworzy obiekt COM, które można zaimplementować interfejsu COM.|
|[com_interface_entry —](com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|
|[implements_category](implements-category.md)|Określa kategorii składników zaimplementowane dla klasy.|
|[progid](progid.md)|Określa identyfikator ProgID kontrolki.|
|[rdx](rdx.md)|Tworzy lub modyfikuje klucz rejestru.|
|[registration_script](registration-script.md)|Wykonuje skrypt określoną rejestrację.|
|[requires_category](requires-category.md)|Określa wymagany składnik kategorie dla klasy.|
|[support_error_info](support-error-info.md)|Obsługuje raportowanie błędów dla obiektu docelowego.|
|[synchronize](synchronize.md)|Synchronizuje dostęp do metody.|
|[Wątkowość](threading-cpp.md)|Określa model wątkowości dla obiektu COM.|
|[vi_progid](vi-progid.md)|Określa identyfikator ProgID niezależny od wersji dla formantu.|
  
## <a name="see-also"></a>Zobacz też

[Atrybuty według grup](attributes-by-group.md)