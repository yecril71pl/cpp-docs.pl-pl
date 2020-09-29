---
title: Implementacja podwójnego interfejsu (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: 97d8cd912c85a74f3550a9ca6c7b87a9717d4075
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499547"
---
# <a name="implementing-a-dual-interface"></a>Implementowanie podwójnego interfejsu

Można zaimplementować podwójny interfejs przy użyciu klasy [IDispatchImpl](../atl/reference/idispatchimpl-class.md) , która zapewnia domyślną implementację `IDispatch` metod w podwójnym interfejsie. Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Aby użyć tej klasy:

- Zdefiniuj Interfejs podwójny w bibliotece typów.

- Utwórz klasę z specjalizacji `IDispatchImpl` (Przekaż informacje o interfejsie i bibliotece typów jako argumenty szablonu).

- Dodaj wpis (lub wpisy) do mapy COM, aby uwidocznić podwójny interfejs za pomocą `QueryInterface` .

- Zaimplementuj częściową tablicę interfejsu w klasie.

- Upewnij się, że biblioteka typów zawierająca definicję interfejsu jest dostępna dla obiektów w czasie wykonywania.

## <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL

Jeśli chcesz utworzyć nowy interfejs i nową klasę do wdrożenia, można użyć [okna dialogowego ATL Add Class](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box), a następnie [Kreatora prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu

Jeśli masz istniejący interfejs, możesz użyć [Kreatora implementacji interfejsu](../atl/reference/adding-a-new-interface-in-an-atl-project.md) , aby dodać niezbędną klasę bazową, wpisy mapy com i implementacje metod szkieletowych do istniejącej klasy.

> [!NOTE]
> Może być konieczne dostosowanie wygenerowanej klasy bazowej tak, aby główne i pomocnicze numery wersji biblioteki typów były przekazane jako argumenty szablonu do `IDispatchImpl` klasy podstawowej. Kreator implementacji interfejsu nie sprawdza numeru wersji biblioteki typów.

## <a name="implementing-idispatch"></a>Implementowanie elementu IDispatch

`IDispatchImpl`Aby zapewnić implementację dispinterface, można użyć klasy bazowej, określając odpowiedni wpis w mapie com (przy użyciu makra [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) lub [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) ), o ile istnieje biblioteka typów opisująca odpowiedni podwójny interfejs. Wdrożenie interfejsu w ten sposób jest dość powszechne `IDispatch` . Kreator prostych obiektów ATL i Kreator implementacji interfejsu założono, że zamierzasz zaimplementować `IDispatch` w ten sposób, aby dodać odpowiedni wpis do mapy.

> [!NOTE]
> ATL oferuje klasy [IDispEventImpl](../atl/reference/idispeventimpl-class.md) i [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) , które ułatwiają zaimplementowanie dispinterfaces bez konieczności używania biblioteki typów zawierającej definicję zgodnego podwójnego interfejsu.

## <a name="see-also"></a>Zobacz też

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
