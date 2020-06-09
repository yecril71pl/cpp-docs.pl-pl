---
title: 'Kontrolki ActiveX MFC: właściwości'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: c7ed0fddea660409f5089159b71d39a29b01d538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618184"
---
# <a name="mfc-activex-controls-properties"></a>Kontrolki ActiveX MFC: właściwości

Kontrolka ActiveX wyzwala zdarzenia w celu komunikowania się z jego kontenerem sterowania. Kontener, w Return, używa metod i właściwości do komunikacji z kontrolką. Metody i właściwości są podobne do użycia i celu odpowiednio do funkcji składowych i zmiennych składowych klasy języka C++. Właściwości są elementami członkowskimi danych kontrolki ActiveX, które są dostępne dla dowolnego kontenera. Właściwości udostępniają interfejs dla aplikacji, które zawierają kontrolki ActiveX, takie jak klienci automatyzacji i kontenery kontrolek ActiveX.

Właściwości są również nazywane atrybutami.

Aby uzyskać więcej informacji na temat metod formantów ActiveX, zobacz artykuł [MFC ActiveX formantów: Methods](mfc-activex-controls-methods.md).

Formanty ActiveX mogą implementować zarówno własne, jak i niestandardowe metody i właściwości. Klasa `COleControl` zawiera implementację właściwości podstawowych. (Aby uzyskać pełną listę właściwości podstawowych, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie właściwości](mfc-activex-controls-adding-stock-properties.md)standardowych). Właściwości niestandardowe zdefiniowane przez dewelopera Dodaj wyspecjalizowane funkcje do kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC: Dodawanie właściwości niestandardowych](mfc-activex-controls-adding-custom-properties.md).

Właściwości niestandardowe i podstawowe, takie jak metody, są obsługiwane przez mechanizm, który składa się z mapy wysyłania, która obsługuje właściwości i metody oraz istniejące funkcje składowe `COleControl` klasy. Ponadto te właściwości mogą mieć parametry używane przez dewelopera do przekazywania dodatkowych informacji do kontrolki.

W poniższych artykułach szczegółowo omówiono właściwości kontrolki ActiveX:

- [Kontrolki ActiveX MFC: dodawanie właściwości standardowych](mfc-activex-controls-adding-stock-properties.md)

- [Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych](mfc-activex-controls-adding-custom-properties.md)

- [Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych](mfc-activex-controls-advanced-property-implementation.md)

- [Kontrolki ActiveX MFC: uzyskiwanie dostępu do właściwości otaczających](mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
