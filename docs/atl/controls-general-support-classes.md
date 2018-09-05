---
title: 'Kontrolki ATL: Ogólne klasy obsługi | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.controls
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18bf4bf2d2081402762026d6f26bd4650f9908fe
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751449"
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

