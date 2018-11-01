---
title: 'ATL kontrolki: Ogólne klasy obsługi'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.controls
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
ms.openlocfilehash: 49b7ff751db33ce2647ea7d4865ebea93949813b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551440"
---
# <a name="controls-general-support-classes"></a>Kontrolki: Ogólne klasy obsługi

Następujące klasy zapewniają ogólną pomoc techniczną dla kontrolek ATL:

- [CComControl](../atl/reference/ccomcontrol-class.md) składa się z pomocy funkcji i danych elementów członkowskich, które są niezbędne do kontrolek ATL.

- [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) udostępnia metody wymagane dla formantów.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) zapewnia metody podmiotu zabezpieczeń, za pomocą których kontener komunikuje się za pomocą kontrolki. Zarządza Aktywacja i dezaktywacja kontrolek w miejscu.

- [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) łączy inicjowania w pojedyncze wywołanie, aby pomóc uniknąć opóźnień, podczas ładowania formantów kontenerów.

- [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) zapewnia interakcji z myszą minimalny dla formantu w przeciwnym razie nieaktywne.

## <a name="sample-program"></a>Przykładowy Program

[ATLFire](../visual-cpp-samples.md)

## <a name="related-articles"></a>Powiązane artykuły

[ALT — samouczek](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../atl/atl-class-overview.md)

