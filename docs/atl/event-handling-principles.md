---
title: Obsługa zasad (ATL) zdarzeń
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: e460685d17a568d9e3b49af40dd1e3f1dbda7c28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610993"
---
# <a name="event-handling-principles"></a>Reguły obsługi zdarzeń

Istnieją trzy kroki wspólne dla wszystkich obsługi zdarzeń. Konieczne będzie:

- Zaimplementuj interfejs zdarzenia dla obiektu.

- Aby źródło zdarzenia obiektu chce odbierać zdarzenia.

- Unadvise źródła zdarzeń, gdy obiekt nie musi już odbierać zdarzenia.

Sposób, że będzie implementować interfejs zdarzenia będzie zależeć od jego typu. Interfejs zdarzeń może być vtable, lub dispinterface. To Ty projektanta źródła zdarzeń, aby zdefiniować interfejs; to Ty można zaimplementować ten interfejs.

> [!NOTE]
>  Mimo że nie ma żadnych techniczne powodów, które interfejs zdarzeń nie może być podwójna, istnieje wiele możliwych przyczyn dobrego projektowania, aby uniknąć użycia duals. Jest to jednak decyzji przez projektanta/implementujący zdarzenia *źródła*. Ponieważ pracujesz z punktu widzenia zdarzenia `sink`, konieczne jest zezwolenie na możliwość utracić dowolnej, ale aby zaimplementować interfejs dwa zdarzenia. Aby uzyskać więcej informacji na temat dwa interfejsy, zobacz [podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md).

Wniosku źródło zdarzenia można podzielić na trzy kroki:

- Zapytania do obiektu źródłowego [interfejsy IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Wywołaj [IConnectionPointContainer::FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) przekazywanie identyfikatora IID interfejsu zdarzenia, który Cię interesuje. Jeśli operacja się powiedzie, spowoduje to zwrócenie [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) interfejs dla obiektu punktu połączenia.

- Wywołaj [IConnectionPoint::Advise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-advise) przekazywanie `IUnknown` obiektu sink zdarzenia. Jeśli operacja się powiedzie, spowoduje to zwrócenie `DWORD` plik cookie reprezentującą połączenie.

Po pomyślnym zarejestrowaniu zainteresowanie odbierania zdarzeń metod na interfejs zdarzenia obiektu będzie miała nazwę zgodnie ze zdarzenia wywoływane przez obiekt źródłowy. Jeśli nie potrzebujesz już do odbierania zdarzeń, można przekazać pliku cookie do punktu połączenia za pośrednictwem [IConnectionPoint::Unadvise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Spowoduje to przerwanie połączenia między źródła i ujścia.

Uważaj uniknąć odwołania cykli podczas obsługi zdarzeń.

## <a name="see-also"></a>Zobacz też

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)

