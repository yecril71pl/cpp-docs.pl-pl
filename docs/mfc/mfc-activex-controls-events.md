---
title: 'Formanty MFC ActiveX: Zdarzenia | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6760f2051542a28e78f5f8f2fa81f6937388d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-events"></a>Kontrolki ActiveX MFC: zdarzenia
Kontrolki ActiveX użyć zdarzeń, aby powiadomić kontener, który ma coś się stało z formantem. Typowe zdarzenia przykładami kliknięć w formancie dane wprowadzane przy użyciu klawiatury i zmiany w stanie formantu. Gdy są wykonywane następujące akcje, formantu wyzwala zdarzenie powiadamiania w kontenerze.  
  
 Zdarzenia są również nazywane wiadomości.  
  
 MFC obsługuje dwa rodzaje zdarzeń: standardowych i niestandardowych. Te zdarzenia, które klasy są zdarzeń standardowych [colecontrol —](../mfc/reference/colecontrol-class.md) obsługuje automatycznie. Aby uzyskać pełną listę zdarzeń standardowych, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie zdarzeń giełdowych](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Zdarzenia niestandardowe umożliwiają formantu możliwość powiadamiania kontenera akcji określone dla tego formantu. Przykłady byłoby zmiany wewnętrzny stan klasy formantu lub odebranie komunikatu okna.  
  
 Dla formantu do uruchamiania zdarzeń poprawnie Twojej klasy kontrolki zamapuj każdego zdarzenia formantu do funkcji członkowskiej, która powinna być wywoływana po wystąpieniu zdarzenia pokrewne. Ten mechanizm mapowania (nazywane mapę zdarzeń) centralizuje informacje o zdarzeniu i umożliwia programowi Visual Studio do łatwego dostępu i manipulowania zdarzeń formantu. Ta mapa zdarzeń jest deklarowany przez następujące makra, znajduje się w nagłówku (. H) pliku deklaracja klasy formantu:  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]  
  
 Po Mapa zdarzeń został zadeklarowany, muszą być zdefiniowane w implementacji formantu (. Pliku CPP). Następujące wiersze kodu zdefiniować Mapa zdarzeń, dzięki czemu formantu uruchomienie określonych zdarzeń:  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]  
  
 Jeśli używasz Kreator kontrolek ActiveX MFC do tworzenia projektu, automatycznie dodaje te wiersze. Jeśli nie używasz, Kreator kontrolek ActiveX MFC, można ręcznie dodać te wiersze.  
  
 Widok klas, można dodawać standardowych zdarzeń obsługiwaną przez klasę `COleControl` lub niestandardowych zdarzeń zdefiniowanych przez użytkownika. Dla każdego nowego zdarzenia widoku klasy automatycznie dodaje poprawnego wpisu mapy zdarzeń formantu i formantu. Plik IDL.  
  
 Zdarzenia szczegółowo omówiono w nim dwa inne artykuły:  
  
-   [Formanty MFC ActiveX: Dodawanie zdarzeń standardowych](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Kontrolki ActiveX MFC: dodawanie zdarzeń niestandardowych](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [Klasa COleControl](../mfc/reference/colecontrol-class.md)
