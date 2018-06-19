---
title: 'Formanty MFC ActiveX: Właściwości | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: ac9d9e4f5e7d777bd147ce36e970e7a30fd875b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347110"
---
# <a name="mfc-activex-controls-properties"></a>Kontrolki ActiveX MFC: właściwości
Kontrolki ActiveX generowane zdarzeń do komunikowania się z jego formantu kontenera. Kontener, w zamian używa metody i właściwości do komunikowania się z formantem. Metody i właściwości są podobne w użycie i cel, odpowiednio do funkcji Członkowskich i zmiennych Członkowskich klasy C++. Właściwości są członkami danych formantu ActiveX, które są widoczne dla żadnych kontenera. Właściwości zapewniają interfejs do aplikacji, które zawierają kontrolki ActiveX, takich jak klienci automatyzacji i kontenery formantów ActiveX.  
  
 Właściwości są również nazywane atrybutów.  
  
 Aby uzyskać więcej informacji na temat metod formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md).  
  
 Formanty ActiveX można zaimplementować giełdowych i niestandardowych metod i właściwości. Klasa `COleControl` udostępnia implementację dla właściwości standardowych. (Aby uzyskać pełną listę właściwości podstawowych, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie właściwości zasobu](../mfc/mfc-activex-controls-adding-stock-properties.md).) Właściwości niestandardowe zdefiniowane przez dewelopera, Dodaj specjalnych funkcji do formantu ActiveX. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC: Dodawanie właściwości niestandardowych](../mfc/mfc-activex-controls-adding-custom-properties.md).  
  
 Właściwości standardowych i niestandardowych, takich jak metod, są obsługiwane przez mechanizm, który składa się z mapy wysyłania obsługująca właściwości i metod i istniejące funkcje Członkowskie `COleControl` klasy. Ponadto te właściwości mogą mieć parametry używane przez projektanta do przekazania dodatkowych informacji do formantu.  
  
 Właściwości formantu ActiveX bardziej szczegółowo omówiono w nim następujące artykuły:  
  
-   [Kontrolki ActiveX MFC: dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Kontrolki ActiveX MFC: dodawanie właściwości niestandardowych](../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych](../mfc/mfc-activex-controls-advanced-property-implementation.md)  
  
-   [Kontrolki ActiveX MFC: uzyskiwanie dostępu do właściwości otaczających](../mfc/mfc-activex-controls-accessing-ambient-properties.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

