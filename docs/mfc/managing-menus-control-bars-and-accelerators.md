---
title: "Zarządzanie menu, paskami sterowania i akceleratorami | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74b026f273eec0bc689cc6959890b07beb570893
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Zarządzanie menu, paskami sterowania i akceleratorami
Okno ramowe zarządza aktualizowanie obiektów interfejsu użytkownika, w tym menu, przycisków paska narzędzi, pasek stanu i akceleratorami. Umożliwia także zarządzanie na pasku menu MDI aplikacji do udostępniania.  
  
## <a name="managing-menus"></a>Zarządzanie menu  
 Okno ramowe uczestniczy w aktualizowanie elementów interfejsu użytkownika za pomocą `ON_UPDATE_COMMAND_UI` mechanizm opisane w [jak obiekty interfejsu użytkownika aktualizacji](../mfc/how-to-update-user-interface-objects.md). Przyciski na paski narzędzi i innych paski kontrolki są aktualizowane podczas wykonywania pętli bezczynności. Elementy menu w menu rozwijanych na pasku menu są aktualizowane tuż przed menu górnego poziomu.  
  
 Dla aplikacji MDI ramkę okna MDI zarządza paska menu i podpis. Ramka okna MDI jest właścicielem co domyślne menu używany jako paska menu, gdy nie ma żadnych aktywnych okien podrzędnych MDI. Gdy istnieją aktywne elementy podrzędne, pasek menu Okno ramowe MDI zostanie przejęty menu dla aktywnego okna podrzędnego MDI. W przypadku aplikacji MDI obsługuje wiele typów dokumentów, takich jak dokumenty wykresu i arkusza, każdego typu umieszcza własną menu paska menu i zmieni podpis główną ramkę okna.  
  
 [Cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md) zawiera domyślne implementacje dla standardowych poleceń w wyświetlonym menu okna dla aplikacji MDI. W szczególności, nowe okno polecenia (**id_window_new —**) jest zaimplementowana, aby utworzyć nowe okno ramowe i widoku w bieżącym dokumencie. Należy zastąpić tych implementacji tylko wtedy, gdy potrzebujesz Dostosowywanie zaawansowane.  
  
 Wiele okien podrzędnych MDI tego samego typu dokumentu udostępniać zasoby menu. Jeśli kilka okien podrzędnych MDI są tworzone przez tego samego szablonu dokumentu, wszystkie użyciem tego samego zasobu menu zapisywania zasobów systemowych w systemie Windows.  
  
## <a name="managing-the-status-bar"></a>Zarządzanie na pasku stanu  
 Okno ramowe również pozycji na pasku stanu wewnątrz obszaru klienckiego i zarządza stan paska wskaźników. Czyści okno ramowe i aktualizuje obszarze wiadomości w pasku stanu, w razie potrzeby i wyświetla monit ciągi jako użytkownik wybierze elementów menu lub przycisków paska narzędzi zgodnie z opisem w [sposób wyświetlania informacji o poleceniu na pasku stanu](../mfc/how-to-display-command-information-in-the-status-bar.md).  
  
## <a name="managing-accelerators"></a>Zarządzanie akceleratorami  
 Każde okno ramowe przechowuje tabeli akceleratora opcjonalne, który klawiatury akceleratora Translacja zostanie automatycznie. Ten mechanizm ułatwia określenie klawisze skrótów (nazywanych również klawiszy skrótu), które wywołują polecenia menu.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

