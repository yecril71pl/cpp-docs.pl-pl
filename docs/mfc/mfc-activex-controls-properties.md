---
title: 'Kontrolki ActiveX MFC: Właściwości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27cdbd548366bcf02e2d6282b309402cf25af2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401618"
---
# <a name="mfc-activex-controls-properties"></a>Kontrolki ActiveX MFC: właściwości

Kontrolki ActiveX uruchamia zdarzeń do komunikowania się z jego kontenerem kontroli. Kontener, w zamian używa metody i właściwości do komunikowania się za pomocą kontrolki. Metody i właściwości są podobne w użycie i przeznaczenie, odpowiednio do elementów członkowskich i zmienne składowe klasy języka C++. Właściwości są elementy członkowskie danych formantu ActiveX, które są widoczne dla żadnych kontenerów. Właściwości zapewniają interfejs do aplikacji, które zawierają formanty ActiveX, takich jak klienci automatyzacji i kontenery kontrolek ActiveX.

Właściwości są również nazywane atrybutów.

Aby uzyskać więcej informacji na temat metod formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md).

Kontrolki ActiveX można zaimplementować zapasów i niestandardowych metod i właściwości. Klasa `COleControl` dostarcza implementację dla właściwości podstawowe. (Aby uzyskać pełną listę właściwości podstawowe, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie właściwości podstawowe](../mfc/mfc-activex-controls-adding-stock-properties.md).) Właściwości niestandardowe zdefiniowane przez dewelopera, Dodaj wyspecjalizowane funkcje do kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC: Dodawanie właściwości niestandardowych](../mfc/mfc-activex-controls-adding-custom-properties.md).

Standardowych i niestandardowych właściwości, takie jak metody, są obsługiwane przez mechanizm, który składa się z Mapa wysyłania, który obsługuje właściwości i metod oraz istniejące funkcje elementów członkowskich `COleControl` klasy. Ponadto te właściwości mogą mieć parametrów używanych przez dewelopera do przekazania dodatkowych informacji do kontrolki.

W następujących artykułach omówiono właściwości formantu ActiveX bardziej szczegółowo:

- [Kontrolki ActiveX MFC: dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [Kontrolki ActiveX MFC: uzyskiwanie dostępu do właściwości otaczających](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

