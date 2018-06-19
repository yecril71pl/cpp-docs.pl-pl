---
title: 'Menu i zasoby: scalanie Menu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 252619872fc53e06629a4cbded7e3640131dc94a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351969"
---
# <a name="menus-and-resources-menu-merging"></a>Menu i zasoby: scalanie menu
W tym artykule szczegółowo kroki niezbędne do dokumenty i aplikacje OLE do obsługi edycji i aktywacja w miejscu poprawnie. Aktywacja w miejscu stanowi wyzwanie dla kontenera i serwera aplikacji (składnik). Użytkownik pozostaje w tym samym oknie ramki (w kontekście kontenerem), ale jest uruchomiona inna aplikacja (serwer). Wymaga to koordynację między zasobami kontenera i serwera aplikacji.  
  
 Omówione w tym artykule tematy obejmują:  
  
- [Układów menu](#_core_menu_layouts)  
  
- [Paski narzędzi i paski stanu](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a> Układów menu  
 Pierwszym krokiem jest koordynowanie układów menu. Aby uzyskać więcej informacji, zobacz **tworzenie Menu** sekcji [zagadnienia dotyczące Menu programowania](https://msdn.microsoft.com/library/ms647557.aspx) w zestawie Windows SDK.  
  
 Aplikacje kontenera należy utworzyć nowe menu do użycia tylko wtedy, gdy elementy osadzone zostaną aktywowane w miejscu. Co najmniej to menu powinien składać się z następujących czynności w podanej kolejności:  
  
1.  Taki sam jak użyte podczas pliki są otwarte menu Plik. (Zazwyczaj inne elementy menu są umieszczane przed następny element.)  
  
2.  Dwa kolejne separatorów.  
  
3.  Taki sam jak użyte podczas pliki są otwarte menu okna (tylko w przypadku aplikacji kontenera w aplikacji MDI). Niektóre aplikacje mogą mieć inne menu, takich jak menu opcji należących do tej grupy, które pozostanie w menu, gdy element osadzony jest aktywny w miejscu.  
  
    > [!NOTE]
    >  Mogą istnieć inne menu, które mają wpływ na widoku dokumentu kontenera, takich jak powiększenia. Te menu kontenera są wyświetlane między dwa separatory w tego zasobu menu.  
  
 Aplikacje serwera (składnik) również należy utworzyć nowe menu specjalnie z myślą o aktywacji w miejscu. Należy go, podobnie jak menu używany, gdy pliki są otwarte, ale bez elementów menu, takich jak plik i okna, które przekształcać dokument serwera, a nie dane. Zwykle w tym menu składa się z następujących czynności:  
  
1.  Taki sam jak użyte podczas pliki są otwarte menu Edycja.  
  
2.  Separator.  
  
3.  Edycja menu, takich jak menu Pióro w przykładowej aplikacji bazgrołów obiektu.  
  
4.  Separator.  
  
5.  Menu Pomoc.  
  
 Na przykład przyjrzeć się układ niektóre przykładowe menu w miejscu dla kontenera i serwera. Aby jaśniejszy przykłady zostały usunięte szczegóły każdego elementu menu. Menu w miejscu kontenera zawiera następujące wpisy:  
  
```  
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&File C1"  
    MENUITEM SEPARATOR  
    POPUP "&Zoom C2"  
    MENUITEM SEPARATOR  
    POPUP "&Options C3"  
    POPUP "&Window C3"  
END  
```  
  
 Kolejne separatorów wskazuje, gdzie pierwsza część menu serwera. Teraz przyjrzeć się menu w miejscu serwera:  
  
```  
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&Edit S1"  
    MENUITEM SEPARATOR  
    POPUP "&Format S2"  
    MENUITEM SEPARATOR  
    POPUP "&Help S3"  
END  
```  
  
 W tym miejscu separatorów wskazują, gdzie drugiej grupy elementów menu kontenera. Wynikowa struktura menu podczas aktywacji w miejscu wewnątrz tego kontenera obiektu z tego serwera wygląda następująco:  
  
```  
BEGIN  
    POPUP "&File C1"  
    POPUP "&Edit S1"  
    POPUP "&Zoom C2"  
    POPUP "&Format S2"  
    POPUP "&Options C3  
    POPUP "&Window C3"  
    POPUP "&Help S3"  
END  
```  
  
 Jak widać, separatory zostały zamienione na różne grupy menu każdej aplikacji.  
  
 Tabele akceleratora skojarzone z menu w miejscu należy dostarczyć także przez aplikację serwera. Kontener będzie włączyć je do tabel akceleratora.  
  
 Po aktywowaniu element osadzony w miejscu platformę ładuje menu w miejscu. Następnie prosi aplikacji serwera w menu o aktywacji w miejscu i wstawia go skutkującej separatorów. Jest to, jak łączyć menu. Możesz uzyskać menu z kontenera na umieszczanie plików i okno i możesz uzyskać menu z serwera działających w elemencie.  
  
##  <a name="_core_toolbars_and_status_bars"></a> Paski narzędzi i paski stanu  
 Aplikacje serwera należy utworzyć nowy pasek narzędzi i zapisać jego mapy bitowej w osobnym pliku. Aplikacje generowane przez Kreatora aplikacji tej mapy bitowej są przechowywane w pliku o nazwie ITOOLBAR. BMP. Nowy pasek narzędzi zastępuje narzędzi aplikacji kontenera po elementu z serwera w miejscu i powinien zawierać te same elementy jako normalne paska narzędzi, jednak usunąć ikony reprezentujący elementy w menu Plik i okna.  
  
 Ten pasek narzędzi jest ładowany w Twojej `COleIPFrameWnd`-klasy tworzone przez Kreatora aplikacji. Na pasku stanu jest obsługiwany przez kontener aplikacji. Aby uzyskać więcej informacji o implementacji okna ramowe w miejscu, zobacz [serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)   
 [aktywacji](../mfc/activation-cpp.md)   
 [Serwery](../mfc/servers.md)   
 [Kontenery](../mfc/containers.md)

