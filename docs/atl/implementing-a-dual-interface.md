---
title: Implementacja podwójnego interfejsu (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: a85597adad045bee3edb5cc3ed63c72a22fa08fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319464"
---
# <a name="implementing-a-dual-interface"></a>Implementacja podwójnego interfejsu

Można zaimplementować podwójny interfejs przy użyciu [IDispatchImpl](../atl/reference/idispatchimpl-class.md) `IDispatch` klasy, która zapewnia domyślną implementację metod w interfejsie dual. Aby uzyskać więcej informacji, zobacz [Implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Aby użyć tej klasy:

- Zdefiniuj podwójny interfejs w bibliotece typów.

- Wywodź klasę ze `IDispatchImpl` specjalizacji (przekaż informacje o interfejsie i bibliotece typów jako argumenty szablonu).

- Dodaj wpis (lub wpisy) do mapy COM, `QueryInterface`aby udostępnić podwójny interfejs za pośrednictwem programu .

- Zaimplementuj część interfejsu vtable w klasie.

- Upewnij się, że biblioteka typów zawierająca definicję interfejsu jest dostępna dla obiektów w czasie wykonywania.

## <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL

Aby utworzyć nowy interfejs i nową klasę do jego zaimplementowania, można użyć [okna dialogowego Atl Add Class](../ide/add-class-dialog-box.md), a następnie [Kreatora obiektów prostych ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu

Jeśli masz istniejący interfejs, można użyć [Kreatora implementacji interfejsu,](../atl/reference/adding-a-new-interface-in-an-atl-project.md) aby dodać niezbędną klasę podstawową, wpisy mapy COM i implementacje metody szkieletu do istniejącej klasy.

> [!NOTE]
> Może być konieczne dostosowanie wygenerowanej klasy podstawowej, tak aby główne i pomocnicze numery `IDispatchImpl` wersji biblioteki typów były przekazywane jako argumenty szablonu do klasy podstawowej. Kreator implementacji interfejsu nie sprawdza numeru wersji biblioteki typów.

## <a name="implementing-idispatch"></a>Wdrażanie IDispatch

Klasy podstawowej `IDispatchImpl` można użyć, aby zapewnić implementację dispinterface tylko określając odpowiedni wpis na mapie COM (przy użyciu [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) lub [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) makra), tak długo, jak masz biblioteki typów opisujących odpowiedni interfejs podwójny. Jest to dość powszechne, aby zaimplementować interfejs w `IDispatch` ten sposób, na przykład. Kreator obiektów prostych atl i Kreator interfejsu implementacji `IDispatch` zarówno zakłada, że zamierzasz zaimplementować w ten sposób, więc doda odpowiedni wpis do mapy.

> [!NOTE]
> ATL oferuje [IDispEventImpl](../atl/reference/idispeventimpl-class.md) i [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) klasy, które ułatwiają implementowanie dispinterfaces bez konieczności biblioteki typów zawierającej definicję zgodnego interfejsu dual.

## <a name="see-also"></a>Zobacz też

[Dwa interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
