---
title: 'Formanty MFC ActiveX: Metody | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e3b343b13118930612e4adfed4c33a65a9e7be8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-methods"></a>Kontrolki ActiveX MFC: metody
Kontrolki ActiveX wyzwala zdarzenia do komunikacji między sobą i jego formantu kontenera. Kontener mogą również komunikować się za pomocą formantu za pomocą metody i właściwości. Metody są również nazywane funkcji.  
  
 Metody i właściwości Podaj wyeksportowanego interfejsu do użytku przez inne aplikacje, takie jak klienci automatyzacji i kontenery formantów ActiveX. Aby uzyskać więcej informacji na temat właściwości formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md).  
  
 Metody są podobne do używania oraz cel do funkcji Członkowskich klasy C++. Istnieją dwa typy metod formantu można zaimplementować: standardowych i niestandardowych. Podobna do akcji zdarzenia, metod akcji są tych metod, dla którego [colecontrol —](../mfc/reference/colecontrol-class.md) udostępnia implementację. Więcej informacji na temat standardowych metod, zobacz artykuł [kontrolki ActiveX MFC: dodawanie metod giełdowych](../mfc/mfc-activex-controls-adding-stock-methods.md). Metod niestandardowych zdefiniowanych przez deweloperów, Zezwalaj na dodatkowe dostosowanie formantu. Aby uzyskać więcej informacji, zobacz artykuł [kontrolki ActiveX MFC: dodawanie metod niestandardowych](../mfc/mfc-activex-controls-adding-custom-methods.md).  
  
 Biblioteka Microsoft Foundation Class (MFC) implementuje mechanizm umożliwiający formantu do obsługi giełdowych i niestandardowych metod. Pierwsza część jest klasa `COleControl`. Pochodną `CWnd`, `COleControl` funkcje Członkowskie obsługuje standardowych metod, które są wspólne dla wszystkich kontrolek ActiveX. Druga część to mechanizm jest mapy wysyłania. Mapy wysyłania jest podobny do mapy komunikatów; Jednak zamiast mapowania funkcji do systemu Windows Identyfikatora komunikatu, mapy wysyłania mapuje wirtualnych funkcji Członkowskich identyfikatorów IDispatch.  
  
 Kontrolki do obsługi różnych metod poprawnie jej klasa musi zadeklarować mapy wysyłania. Jest to osiągane przez następujący wiersz kodu znajdujący się w nagłówku klasy formantu (. H) plików:  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]  
  
 Głównym celem mapy wysyłania jest ustanowienie relacji między nazwami metody używane przez zewnętrzne wywołującego (na przykład kontener) i funkcji elementów członkowskich klasy formantu, które implementują metody. Po zadeklarowaniu mapy wysyłania musi być zdefiniowane w implementacji formantu (. Pliku CPP). Następujące wiersze kodu zdefiniować mapy wysyłania:  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]  
  
 Jeśli używasz [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) Aby utworzyć projekt, te wiersze zostały dodane automatycznie. Jeśli Kreator formantów MFC ActiveX nie był używany, można ręcznie dodać te wiersze.  
  
 Metody szczegółowo omówiono w nim następujące artykuły:  
  
-   [Kontrolki ActiveX MFC: dodawanie metod standardowych](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Kontrolki ActiveX MFC: dodawanie metod niestandardowych](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Kontrolki ActiveX MFC: zwracanie kodów błędów z metody](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

