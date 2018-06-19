---
title: Praca z obiektami okien | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4c00649c51e34bbbac7adbf7aa5f3c7d04790ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383370"
---
# <a name="working-with-window-objects"></a>Praca z obiektami okien
Praca z systemu windows wymaga dwa rodzaje działań:  
  
-   Obsługa komunikatów systemu Windows  
  
-   Rysowanie w oknie  
  
 Do obsługi komunikatów systemu Windows w dowolnym oknie, w tym własne podrzędne systemu windows, temacie [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md) do mapy wiadomości do klasy okna języka C++. Następnie wpisz obsługi wiadomości funkcji Członkowskich w klasie.  
  
 Większość rysowania w ramach aplikacji występuje w widoku, którego [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcja członkowska jest wywoływana, gdy musi zostać narysowany zawartość okna. Jeśli okno jest elementem podrzędnym widoku, może przekazywać niektóre rysunku widoku do okna podrzędnego dzięki użyciu `OnDraw` wywoływanie jednego funkcji Członkowskich z okna.  
  
 W każdym przypadku należy kontekst urządzenia do rysowania. Można użyć zapasów pióra, pędzla i innych obiektów graficznych zawarte w kontekście urządzenia skojarzone z okna. Lub zmodyfikować te obiekty rysowania efekty, które należy uzyskać. Z kontekstu urządzenia Konfigurowanie Ci się podoba, wywołać elementu członkowskiego funkcje klasy [CDC](../mfc/reference/cdc-class.md) (kontekst urządzenia klasa) do rysowania linii, kształty i tekst; Użyj kolorów; oraz pracy z układ współrzędnych.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)  
  
-   [Rysowanie w widoku](../mfc/drawing-in-a-view.md)  
  
-   [Konteksty urządzenia](../mfc/device-contexts.md)  
  
-   [Obiekty graficzne](../mfc/graphic-objects.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

