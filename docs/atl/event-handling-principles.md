---
title: Zasady obsługi zdarzeń (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 2e810853e7c81f279039e0b3dfda5199d38deee2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319564"
---
# <a name="event-handling-principles"></a>Zasady obsługi zdarzeń

Istnieją trzy kroki typowe dla obsługi wszystkich zdarzeń. Należy:

- Zaimplementuj interfejs zdarzeń na obiekcie.

- Poinformuj źródło zdarzenia, że obiekt chce odbierać zdarzenia.

- Odłącz źródło zdarzeń, gdy obiekt nie musi już odbierać zdarzeń.

Sposób, w jaki zaimplementujesz interfejs zdarzenia, będzie zależeć od jego typu. Interfejs zdarzenia może być vtable, dual lub dispinterface. To do projektanta źródła zdarzeń, aby zdefiniować interfejs; to do Ciebie, aby zaimplementować ten interfejs.

> [!NOTE]
> Chociaż nie ma technicznych powodów, dla których interfejs zdarzenia nie może być podwójny, istnieje wiele dobrych powodów projektowych, aby uniknąć użycia duals. Jest to jednak decyzja podjęta przez projektanta/realizatora *źródła*zdarzenia . Ponieważ pracujesz z perspektywy zdarzenia, `sink`musisz pozwolić na możliwość, że nie masz wyboru, ale zaimplementować interfejs podwójnego zdarzenia. Aby uzyskać więcej informacji na temat dwóch interfejsów, zobacz [Dual Interfaces i ATL](../atl/dual-interfaces-and-atl.md).

Doradztwo na rzecz źródła zdarzeń można podzielić na trzy kroki:

- Kwerenda obiektu źródłowego dla [programu IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Wywołanie [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) przekazywania identyfikator interfejsu zdarzenia, który Cię interesuje. Jeśli to się powiedzie, spowoduje to zwrócenie interfejsu [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) na obiekcie punktu połączenia.

- Wywołanie [IConnectionPoint::Doradzić](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) przekazywanie `IUnknown` sink zdarzenia. Jeśli się powiedzie, `DWORD` spowoduje to zwrócenie pliku cookie reprezentującego połączenie.

Po pomyślnym zarejestrowaniu zainteresowania odbieraniem zdarzeń metody w interfejsie zdarzeń obiektu będą wywoływane zgodnie ze zdarzeniami wywołanymi przez obiekt źródłowy. Jeśli nie trzeba już odbierać zdarzeń, możesz przekazać plik cookie z powrotem do punktu połączenia za pośrednictwem [iConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Spowoduje to przerwanie połączenia między źródłem a umywalką.

Należy uważać, aby uniknąć cykli odniesienia podczas obsługi zdarzeń.

## <a name="see-also"></a>Zobacz też

[Obsługa zdarzeń](../atl/event-handling-and-atl.md)
