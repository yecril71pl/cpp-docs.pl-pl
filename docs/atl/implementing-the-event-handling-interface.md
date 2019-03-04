---
title: Implementowanie interfejsu obsługi zdarzeń
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
ms.openlocfilehash: d977b59907266a2e0141defa8c496b1e7bc66a6c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273416"
---
# <a name="implementing-the-event-handling-interface"></a>Implementowanie interfejsu obsługi zdarzeń

ATL pomaga wszystkie trzy elementy wymagane do obsługi zdarzeń: implementacja interfejsu zdarzenia, wniosku źródła zdarzeń i unadvising źródła zdarzeń. Dokładne kroki, które należy podjąć, zależą od typu interfejsu zdarzenia i wymagania dotyczące wydajności aplikacji.

Najbardziej typowych sposobów implementowania interfejsu przy użyciu biblioteki ATL są:

- Wyprowadzanie z niestandardowego interfejsu.

- Wyprowadzanie z [IDispatchImpl](../atl/reference/idispatchimpl-class.md) dwa interfejsy opisane w bibliotece typów.

- Wyprowadzanie z [IDispEventImpl](../atl/reference/idispeventimpl-class.md) dla dispinterfaces opisanych w bibliotece typów.

- Wyprowadzanie z [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) dla dispinterfaces nie opisano w bibliotece typów, lub jeśli chcesz zwiększyć wydajność przez nie trwa ładowanie informacji o typie w czasie wykonywania.

W przypadku wdrażania niestandardowego lub podwójnego interfejsu źródła zdarzeń należy poinformować, wywołując [AtlAdvise](reference/connection-point-global-functions.md#atladvise) lub [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise). Należy do śledzenia zwracany przez wywołanie pliku cookie. Wywołaj [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) aby przerwać połączenie.

W przypadku wdrażania przy użyciu dispinterface `IDispEventImpl` lub `IDispEventSimpleImpl`, źródła zdarzeń należy poinformować, wywołując [IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise). Wywołaj [IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) aby przerwać połączenie.

Jeśli używasz `IDispEventImpl` jako klasa bazowa kontrolki złożonej wymienione na mapie obiektu sink źródła zdarzeń będzie zalecany unadvised automatycznie przy użyciu [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

`IDispEventImpl` i `IDispEventSimpleImpl` klasy Zarządzanie pliku cookie.

## <a name="see-also"></a>Zobacz także

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)
