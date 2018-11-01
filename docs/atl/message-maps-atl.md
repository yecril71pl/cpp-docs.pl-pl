---
title: Mapy komunikatów (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
ms.openlocfilehash: 92d0b4887127e1803d1d3209a6a1dd51e9a98d15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496112"
---
# <a name="message-maps-atl"></a>Mapy komunikatów (ATL)

Mapy komunikatów kojarzy funkcji obsługi przy użyciu określonego komunikatu, polecenie lub powiadomień. Przy użyciu ATL [makra mapy komunikatów](../atl/reference/message-map-macros-atl.md), można określić mapy komunikatów dla okna. Procedury okna w `CWindowImpl`, `CDialogImpl`, i `CContainedWindowT` przekierowywania komunikatów okna do jego mapie komunikatów.

[Funkcje obsługi komunikatów](../atl/message-handler-functions.md) zaakceptowanie dodatkowych argumentu typu `BOOL&`. Ten argument wskazuje, czy wiadomość została przetworzona, i jest ustawiona na wartość TRUE, domyślnie. Funkcja obsługi można następnie ustawiać na wartość FALSE, aby wskazać, że nie ma obsługi wiadomości. W tym przypadku ATL będą w dalszym ciągu wyszukiwania dla funkcji obsługi dalsze w mapie wiadomości. Ustawiając ten argument na wartość FALSE, należy najpierw wykonać pewne działania w odpowiedzi na wiadomość, a następnie zezwolić na przetwarzanie domyślnego lub innego funkcji obsługi na zakończenie obsługi wiadomości.

## <a name="chained-message-maps"></a>Mapy komunikatów łańcuchowa

ATL również pozwala na łańcuch mapy komunikatów, która kieruje wiadomości obsługi do mapy komunikatów zdefiniowane w innej klasy. Na przykład można zaimplementować typowych komunikatów w osobnej klasy, aby zapewniać jednolite zachowanie dla wszystkich okien łańcucha dla tej klasy. Można połączyć w łańcuch do klasy bazowej lub element członkowski danych klasy.

ATL obsługuje również dynamiczne tworzenie łańcuchów pozwalający do tworzenia łańcucha mapę komunikatów w innym obiektem w czasie wykonywania. Do zaimplementowania dynamicznych łańcucha, musi pochodzić od klasy [CDynamicChain](../atl/reference/cdynamicchain-class.md). Następnie zadeklarować [CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) makra w mapie wiadomości. CHAIN_MSG_MAP_DYNAMIC wymaga unikatowy numer, który identyfikuje obiekt i mapy komunikatów, do którego łańcucha. Należy zdefiniować to unikatowa wartość za pomocą wywołania `CDynamicChain::SetChainEntry`.

Można połączyć w łańcuch do każdej klasy, która deklaruje mapy komunikatów, pod warunkiem klasę pochodną [CMessageMap](../atl/reference/cmessagemap-class.md). `CMessageMap` zezwala na obiekt uwidocznić jej mapy wiadomości do innych obiektów. Należy pamiętać, że `CWindowImpl` już pochodzi od klasy `CMessageMap`.

## <a name="alternate-message-maps"></a>Mapy komunikatów alternatywne

Na koniec ATL obsługuje mapy komunikatów alternatywne, zadeklarowany za pomocą [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) makra. Każdej mapie komunikatów alternatywne jest identyfikowany przez unikatowy numer, który zostanie przekazany do ALT_MSG_MAP. Za pomocą alternatywnej komunikatu mapy, może obsługiwać komunikaty wiele okien w jedną mapę. Należy pamiętać, że domyślnie `CWindowImpl` nie korzysta z mapy komunikatów alternatywne. Aby dodać tę obsługę, Zastąp `WindowProc` method in Class metoda swoje `CWindowImpl`-pochodne klasy i wywołania `ProcessWindowMessage` o identyfikatorze mapy wiadomości.

## <a name="see-also"></a>Zobacz też

[Implementowanie okna](../atl/implementing-a-window.md)

