---
title: Klasy obsługi interfejsu użytkownika (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.ui
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa28c172b4eb22366d2af55d040cb52c9e84a31
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755238"
---
# <a name="ui-support-classes"></a>Klasy obsługi interfejsu użytkownika

Następujące klasy zawierają ogólne Obsługa interfejsu użytkownika:

- [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) interfejs do analizowania Microsoft HTML i aparat renderowania.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) zapewnia metody podmiotu zabezpieczeń, za pomocą których kontener komunikuje się za pomocą kontrolki. Zarządza Aktywacja i dezaktywacja kontrolek w miejscu.

- [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) zarządza ponownej aktywacji w miejscu kontrolek. Umożliwia kontrolce odbierać komunikaty, a także uczestniczyć w operacji przeciągania i upuszczania.

- [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) pomaga komunikacji między formantem w miejscu, a jego kontenera.

- [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) umożliwia kontrolkę do wyświetlania sam bezpośrednio i powiadom kontenera zmiany w jego wyświetlania. Zapewnia obsługę pozbawionej migotania rysowania, formanty innych niż prostokątne i przejrzystości i testowania trafień.

## <a name="related-articles"></a>Powiązane artykuły

[ALT — samouczek](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../atl/atl-class-overview.md)

