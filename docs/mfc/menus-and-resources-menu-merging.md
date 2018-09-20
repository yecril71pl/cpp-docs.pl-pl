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
ms.openlocfilehash: 2f4e76902335477ba507e6f3e7a66c5f862b8543
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418674"
---
# <a name="menus-and-resources-menu-merging"></a>Menu i zasoby: scalanie menu

Ten artykuł szczegółowo opisuje kroki niezbędne do dokumenty i aplikacje OLE do obsługi edycja wizualna i aktywacja w miejscu prawidłowo. Aktywacja w miejscu stanowi wyzwanie dla kontenera i serwera aplikacji (składnik). Użytkownik pozostaje w tym samym oknie ramki (w kontekście dokumentu kontenera), ale jest faktycznie uruchomiona inna aplikacja (serwer). Wymaga to koordynacji między zasobami kontenera i serwera aplikacji.

Tematy omówione w tym artykule obejmują:

- [Układów menu](#_core_menu_layouts)

- [Paski narzędzi i stanu](#_core_toolbars_and_status_bars)

##  <a name="_core_menu_layouts"></a> Układów menu

Pierwszym krokiem jest koordynowanie układów menu. Aby uzyskać więcej informacji, zobacz **tworzenie Menu** sekcji [zagadnienia programowania Menu](https://msdn.microsoft.com/library/ms647557.aspx) w zestawie Windows SDK.

Aplikacje kontenera należy utworzyć nowe menu ma być używany tylko wtedy, gdy elementy osadzone są aktywowane w miejscu. Jako minimum to menu powinna składać się z następujących czynności w podanej kolejności:

1. Menu Plik jest taka sama jak używana, gdy pliki są otwarte. (Zazwyczaj inne elementy menu są umieszczane przed następną.)

1. Dwóch następujących po sobie separatory.

1. Menu okna jest taka sama jak używana, gdy pliki są otwarte (tylko wtedy, gdy aplikacji kontenera w aplikacji MDI). Niektóre aplikacje mogą mieć inne menu, takich jak menu opcji należących do tej grupy, które pozostanie w menu, gdy element osadzony jest aktywowany w miejscu.

    > [!NOTE]
    >  Mogą istnieć inne menu, które wpływają na widok dokumentu kontenera, takich jak powiększenia. Menu tych kontenerów są wyświetlane między dwoma separatorów w tym zasobie menu.

Aplikacje serwera (składnik) również należy utworzyć nowe menu specjalnie dla aktywacji w miejscu. Należy go, podobnie jak menu jest używany, gdy pliki są otwarte, ale bez elementów menu, takich jak plik i okna, w którym manipulowania dokument serwera, a nie dane. Zwykle to menu składa się z następujących czynności:

1. Edytuj menu identyczne z używaną, gdy pliki są otwarte.

1. Separator.

1. Edycja menu, takich jak menu Pióro w przykładowej aplikacji bazgrołów obiektu.

1. Separator.

1. Menu Pomoc.

Na przykład Przyjrzyj się układ niektóre menu w miejscu próbki dla kontenera i serwera. Na przykład bardziej zrozumiały zostały usunięte szczegóły każdego elementu menu. Menu w miejscu kontenera zawiera następujące wpisy:

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

Następujące po sobie separatory wskazują, gdzie pierwszej części menu serwera. Teraz sprawdźmy menu w miejscu serwera:

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

Separatory, w tym miejscu wskazują, gdzie drugiej grupy elementów menu kontenera. Wynikowy struktura menu przy aktywacji obiektu z tego serwera w miejscu, w tym kontenerze wygląda następująco:

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

Jak widać, separatory zostały zastąpione przy użyciu różnych grup menu każdej aplikacji.

Tabele akceleratora skojarzone z menu w miejscu również powinien być dostarczony przez aplikację serwera. Kontener będzie dołączać je do jego własnej tabel akceleratora.

Po aktywowaniu osadzonego elementu w miejscu ramach ładuje menu w miejscu. Następnie prosi aplikacji serwera w celu jego menu o aktywacji w miejscu i wstawia go których separatorów. Jest to, jak połączyć menu. Możesz uzyskać menu z kontenera, wykonywanie operacji na rozmieszczenie plików i okna, a otrzymasz menu z serwera przez wykonywanie operacji na elemencie.

##  <a name="_core_toolbars_and_status_bars"></a> Paski narzędzi i stanu

Aplikacje serwera należy utworzyć nowy pasek narzędzi i zapisać jego mapy bitowej w oddzielnym pliku. Aplikacje generowane przez Kreatora aplikacji zapisanie tej mapy bitowej w pliku o nazwie ITOOLBAR. BMP. Nowy pasek narzędzi zastępuje paska narzędzi aplikacji kontenera, gdy elementu danych na serwerze jest aktywowany w miejscu, powinny zawierać te same elementy, jak normalne paska narzędzi, ale usunięcie ikon reprezentujących elementy w menu Plik i okna.

Ten pasek narzędzi jest ładowany w swojej `COleIPFrameWnd`-klasy, tworzone przez Kreatora aplikacji. Na pasku stanu jest obsługiwane przez aplikację kontenera. Aby uzyskać więcej informacji na temat implementacji okien ramowych w miejscu, zobacz [serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Aktywacja](../mfc/activation-cpp.md)<br/>
[Serwery](../mfc/servers.md)<br/>
[Kontenery](../mfc/containers.md)

