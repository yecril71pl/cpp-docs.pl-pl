---
title: 'Kontrolki ActiveX MFC: Właściwości'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: 5e01854e7ae7acdc33275351d0d26a76dfeabc9b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326416"
---
# <a name="mfc-activex-controls-properties"></a>Kontrolki ActiveX MFC: Właściwości

Kontrolki ActiveX uruchamia zdarzeń do komunikowania się z jego kontenerem kontroli. Kontener, w zamian używa metody i właściwości do komunikowania się za pomocą kontrolki. Metody i właściwości są podobne w użycie i przeznaczenie, odpowiednio do elementów członkowskich i zmienne składowe klasy języka C++. Właściwości są elementy członkowskie danych formantu ActiveX, które są widoczne dla żadnych kontenerów. Właściwości zapewniają interfejs do aplikacji, które zawierają formanty ActiveX, takich jak klienci automatyzacji i kontenery kontrolek ActiveX.

Właściwości są również nazywane atrybutów.

Aby uzyskać więcej informacji na temat metod formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: Metody](../mfc/mfc-activex-controls-methods.md).

Kontrolki ActiveX można zaimplementować zapasów i niestandardowych metod i właściwości. Klasa `COleControl` dostarcza implementację dla właściwości podstawowe. (Aby uzyskać pełną listę właściwości podstawowe, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md).) Właściwości niestandardowe zdefiniowane przez dewelopera, Dodaj wyspecjalizowane funkcje do kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC: Dodawanie właściwości niestandardowych](../mfc/mfc-activex-controls-adding-custom-properties.md).

Standardowych i niestandardowych właściwości, takie jak metody, są obsługiwane przez mechanizm, który składa się z Mapa wysyłania, który obsługuje właściwości i metod oraz istniejące funkcje elementów członkowskich `COleControl` klasy. Ponadto te właściwości mogą mieć parametrów używanych przez dewelopera do przekazania dodatkowych informacji do kontrolki.

W następujących artykułach omówiono właściwości formantu ActiveX bardziej szczegółowo:

- [Kontrolki ActiveX MFC: Dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Kontrolki ActiveX MFC: Dodawanie właściwości niestandardowych](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Kontrolki ActiveX MFC: Implementacja właściwości zaawansowanych](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [Kontrolki ActiveX MFC: Uzyskiwanie dostępu do właściwości otaczających](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
