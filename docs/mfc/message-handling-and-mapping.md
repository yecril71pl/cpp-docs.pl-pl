---
title: Obsługa i mapowanie komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66171c5df636597a2ff6be0438b558dc418b72af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348531"
---
# <a name="message-handling-and-mapping"></a>Obsługa i mapowanie komunikatów
Rodziny tego artykułu opisano, jak komunikaty i polecenia są przetwarzane przez MFC framework i jak łączyć się ich funkcje programu obsługi.  
  
 W przypadku tradycyjnych programów dla systemu Windows komunikaty systemu Windows są obsługiwane w instrukcji switch dużych w procedurę okna. Zamiast tego używa MFC [mapy komunikatów](../mfc/message-categories.md) mapować wiadomości bezpośrednie do funkcji Członkowskich różne klasy. Mapy wiadomości są bardziej efektywne niż funkcji wirtualnych w tym celu, a także zezwalać komunikatów obsługiwanych przez najbardziej odpowiedniego obiektu C++ — aplikacji, dokumentu, widok i tak dalej. Można mapować pojedynczym komunikacie lub zakres komunikatów, identyfikatory poleceń lub kontrolować identyfikatorów.  
  
 **WM_COMMAND** wiadomości — zwykle generowane przez menu, przycisków paska narzędzi lub akceleratorów — również używać mechanizmu mapy komunikatów. MFC definiuje standard [routingu](../mfc/command-routing.md) polecenia komunikatów między aplikacji, ramka okna, widok i dokumenty aktywne w programie. Można zastąpić to routingu, jeśli potrzebujesz.  
  
 Mapy komunikatów podać również sposób aktualizowanie obiektów interfejsu użytkownika (np. menu i przycisków paska narzędzi), włączając lub wyłączając je zgodnie z bieżącego kontekstu.  
  
 Aby uzyskać ogólne informacje na temat wiadomości i kolejki wiadomości w systemie Windows, temacie [wiadomości i kolejki wiadomości](http://msdn.microsoft.com/library/windows/desktop/ms632590) w zestawie Windows SDK.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [Jak struktura wywołuje program obsługi komunikatów](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)  
  
-   [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [Sposób wyświetlania informacji o poleceniu na pasku stanu](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [Aktualizacja dynamiczna obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)  
  
-   [Instrukcje: tworzenie mapy komunikatów dla klasy szablonów](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)   
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)   
 [Klasa CWnd](../mfc/reference/cwnd-class.md)   
 [Klasa CCmdTarget](../mfc/reference/ccmdtarget-class.md)
