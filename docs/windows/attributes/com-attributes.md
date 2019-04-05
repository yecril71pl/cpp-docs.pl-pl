---
title: Atrybuty COM
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: eb87d3861c6b3066cf482108e2ce2243c8196093
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038932"
---
# <a name="com-attributes"></a>Atrybuty COM

Atrybuty COM wstrzyknąć kod obsługujący wiele obszarów projektowania modelu COM i .NET Framework — programowanie środowiska uruchomieniowego języka wspólnego. Te obszary w zakresie od implementacji niestandardowego interfejsu i obsługa istniejące interfejsy do obsługi podstawowe właściwości, metody i zdarzenia. Ponadto pomocy technicznej można znaleźć złożone i implementacją kontrolki ActiveX.

|Atrybut|Opis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Wskazuje, że formant może być agregowany przez inny formant.|
|[aggregates](aggregates.md)|Wskazuje, że formant agreguje klasy docelowej.|
|[coclass](coclass.md)|Tworzy obiekt COM, które można zaimplementować interfejsu COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Dodaje wpis interfejsu do mapy COM.|
|[implements_category](implements-category.md)|Określa kategorii składników zaimplementowane dla klasy.|
|[progid](progid.md)|Określa identyfikator ProgID kontrolki.|
|[rdx](rdx.md)|Tworzy lub modyfikuje klucz rejestru.|
|[registration_script](registration-script.md)|Wykonuje skrypt określoną rejestrację.|
|[requires_category](requires-category.md)|Określa wymagany składnik kategorie dla klasy.|
|[support_error_info](support-error-info.md)|Obsługuje raportowanie błędów dla obiektu docelowego.|
|[synchronize](synchronize.md)|Synchronizuje dostęp do metody.|
|[threading](threading-cpp.md)|Określa model wątkowości dla obiektu COM.|
|[vi_progid](vi-progid.md)|Określa identyfikator ProgID niezależny od wersji dla formantu.|

## <a name="see-also"></a>Zobacz także

[Atrybuty według grup](attributes-by-group.md)