---
title: Kiedy są wywoływane programy obsługi aktualizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d899d9952ae13b23121fb0b7a188f8136315c342
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="when-update-handlers-are-called"></a>Kiedy są wywoływane programy obsługi aktualizacji
Załóżmy, że użytkownik kliknie przycisk myszy w menu Plik, który generuje `WM_INITMENUPOPUP` wiadomości. W ramach mechanizmu aktualizacji zbiorczo aktualizuje wszystkie elementy w menu plik przed menu górnego poziomu, więc użytkownik może go wyświetlić.  
  
 Aby to zrobić, trasy framework zaktualizować polecenia dla wszystkich elementów menu w menu podręcznym wzdłuż standardowego routingu poleceń. Obiekty docelowe poleceń na routingu mógł zaktualizować wszystkie elementy menu, dopasowując polecenia aktualizacji z wpisem odpowiednie mapy komunikatów (w postaci `ON_UPDATE_COMMAND_UI`) i wywołanie funkcji "procedury obsługi aktualizacji". W związku z tym menu z sześciu elementów menu, sześć polecenia aktualizacji są wysyłane. Jeśli istnieje procedura obsługi aktualizacji dla Identyfikatora polecenia elementu menu, jest on nazywany wykonaj aktualizację. Jeśli nie, w ramach sprawdza istnienie obsługi dla tego Identyfikatora polecenia i włącza lub wyłącza element menu, zależnie od potrzeb.  
  
 Jeśli nie znajdzie platformę `ON_UPDATE_COMMAND_UI` wpis podczas routing poleceń, automatycznie umożliwia obiektu interfejsu użytkownika w przypadku `ON_COMMAND` wpis gdzieś o takim samym identyfikatorze polecenia. W przeciwnym razie powoduje wyłączenie obiektu interfejsu użytkownika. W związku z tym aby upewnić się, że obiekt interfejsu użytkownika jest włączona, dostarczyć obsługi dla polecenia, które generuje obiekt lub podać programu obsługi aktualizacji. Zobacz rysunek w temacie [obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md).  
  
 Jest to można wyłączyć domyślnego wyłączenie obiektów interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) elementu członkowskiego klasy `CFrameWnd` w *odwołania MFC*.  
  
 Inicjowanie menu odbywa się automatycznie w ramach występuje, gdy aplikacja odbiera `WM_INITMENUPOPUP` wiadomości. Podczas wykonywania pętli bezczynności struktura wyszukuje polecenia routingu dla przycisku programy obsługi aktualizacji w podobny sposób jak w przypadku menu.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: aktualizowanie obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

