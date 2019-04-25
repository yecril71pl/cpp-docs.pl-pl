---
title: Implementacja podwójnego interfejsu (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: ecd6a0cc90ca4175c4ae898f2e9aa8bf00508a3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262232"
---
# <a name="implementing-a-dual-interface"></a>Implementacja podwójnego interfejsu

Można zaimplementować przy użyciu podwójnego interfejsu [IDispatchImpl](../atl/reference/idispatchimpl-class.md) klasy, która udostępnia domyślną implementację elementu `IDispatch` metody podwójnego interfejsu. Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Aby użyć tej klasy:

- Zdefiniuj podwójnego interfejsu w bibliotece typów.

- Dziedziczyć klasy specjalizacją `IDispatchImpl` (przekazać informacje o bibliotece interfejsu i typ jako argumenty szablonu).

- Dodaj wpis (lub wpisy) do mapy COM do udostępnienia podwójnego interfejsu za pośrednictwem `QueryInterface`.

- Implementowanie vtable część interfejsu w klasie.

- Upewnij się, że biblioteki typów z definicją interfejsu dostępne dla obiektów w czasie wykonywania.

## <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL

Jeśli chcesz utworzyć nowy interfejs i nową klasę do jej wdrożenia, możesz użyć [okno dialogowe Dodawanie klasy ATL](../ide/add-class-dialog-box.md), a następnie [proste Kreator obiektu ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu

Jeśli masz istniejący interfejs, możesz użyć [Kreator implementacji interfejsu](../atl/reference/adding-a-new-interface-in-an-atl-project.md) dodać niezbędne klasy bazowej, wpisy mapy COM i implementacje metod szkielet do istniejącej klasy.

> [!NOTE]
>  Może być konieczne dostosowanie wygenerowanej klasy bazowej, tak, aby numery wersji głównych i pomocniczych biblioteki typów są przekazywane jako argumenty szablonu, aby Twoje `IDispatchImpl` klasy bazowej. Kreator implementacji interfejsu nie Sprawdź numer wersji biblioteki typów.

## <a name="implementing-idispatch"></a>Implementowanie interfejsu IDispatch

Możesz użyć `IDispatchImpl` klasy bazowej na dostarczać implementację dispinterface po prostu, określając odpowiedni wpis w mapie com. (przy użyciu [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) lub [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) — makro) tak długo, jak długo mają bibliotekę typów, opisujący odpowiedniego podwójnego interfejsu. Dość często, aby zaimplementować `IDispatch` interfejsu na przykład w ten sposób. Proste Kreator obiektu ATL i Kreator interfejsu zaimplementować zarówno założono, że zamierzasz wdrożyć `IDispatch` w ten sposób, więc ich będzie dodać odpowiedni wpis do mapy.

> [!NOTE]
>  ATL udostępnia [IDispEventImpl](../atl/reference/idispeventimpl-class.md) i [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) klasy, aby pomóc w zaimplementowaniu dispinterfaces bez konieczności bibliotekę typów z definicją zgodne podwójnego interfejsu.

## <a name="see-also"></a>Zobacz także

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
