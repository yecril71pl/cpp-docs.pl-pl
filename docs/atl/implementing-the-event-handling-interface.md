---
title: Implementowanie interfejsu obsługi zdarzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57e685ea9ac4b1efc76f7657421d825b83f4a9b7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078625"
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

## <a name="see-also"></a>Zobacz też

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)
