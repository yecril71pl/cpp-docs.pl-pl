---
title: Podsumowanie obsługi zdarzeń ATL
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
ms.openlocfilehash: 0e3a47719e3160170ed1bfa64b315415ddc7a1c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252151"
---
# <a name="atl-event-handling-summary"></a>Podsumowanie obsługi zdarzeń ATL

Ogólnie rzecz biorąc Obsługa zdarzeń COM jest stosunkowo prosty proces. Istnieją trzy podstawowe kroki:

- Zaimplementuj interfejs zdarzenia dla obiektu.

- Aby źródło zdarzenia obiektu chce odbierać zdarzenia.

- Unadvise źródła zdarzeń, gdy obiekt nie musi już odbierać zdarzenia.

## <a name="implementing-the-interface"></a>Implementowanie interfejsu

Istnieją cztery główne sposoby implementacji interfejsu, za pomocą ATL.

|Pochodzi od|Odpowiednie dla typu interfejsu|Wymaga wdrożenia wszystkich metod *|Wymaga biblioteki typów w czasie wykonywania|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|Interfejs|Vtable|Yes|Nie|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Podwójne|Yes|Yes|
|[Z interfejsu IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|Nie|Yes|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|Nie|Nie|

\* Korzystając z klasy obsługi biblioteki ATL, nigdy nie należy implementować `IUnknown` lub `IDispatch` metody ręcznie.

## <a name="advising-and-unadvising-the-event-source"></a>Doradztwa i Unadvising źródła zdarzeń

Istnieją trzy główne sposoby wniosku oraz unadvising źródła zdarzeń za pomocą ATL.

|Aby — funkcja|Unadvise — funkcja|Najbardziej odpowiedni do użytku z programem|Wymaga informacji o pliku cookie|Komentarze|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable lub podwójne interfejsy|Tak|`AtlAdvise` jest funkcją globalną ATL. `CComPtrBase::Advise` jest używany przez [CComPtr](../atl/reference/ccomptr-class.md) i [CComQIPtr](../atl/reference/ccomqiptr-class.md).|
|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) lub [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Nie|Mniej parametrów niż `AtlAdvise` ponieważ klasa bazowa wykonuje więcej pracy.|
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|Kontrolki ActiveX w formanty złożone|Nie|`CComCompositeControl::AdviseSinkMap` Zaleca się, że wszystkie wpisy w zdarzeniu ujścia mapy. Tę samą funkcję unadvises wpisów. Ta metoda jest wywoływana automatycznie przez `CComCompositeControl` klasy.|
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|Kontrolki ActiveX w oknie dialogowym|Nie|`CAxDialogImpl::AdviseSinkMap` z informacją o tym i unadvises wszystkich kontrolek ActiveX w zasobu okna dialogowego. Odbywa się to automatycznie dla Ciebie.|

## <a name="see-also"></a>Zobacz także

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)<br/>
[Obsługa interfejsu IDispEventImpl](../atl/supporting-idispeventimpl.md)
