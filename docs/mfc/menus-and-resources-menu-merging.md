---
title: 'Menu i zasoby: scalanie menu'
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: 149af83bd53b7a97fd264bd6b18701fc9f64ea1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364768"
---
# <a name="menus-and-resources-menu-merging"></a>Menu i zasoby: scalanie menu

W tym artykule opisano kroki niezbędne dla aplikacji dokumentów OLE do obsługi edycji wizualnej i aktywacji w miejscu poprawnie. Aktywacja w miejscu stanowi wyzwanie zarówno dla aplikacji kontenerowych, jak i serwerowych (składnikowych). Użytkownik pozostaje w tym samym oknie ramki (w kontekście dokumentu kontenera), ale faktycznie uruchamia inną aplikację (serwer). Wymaga to koordynacji między zasobami aplikacji kontenera i serwera.

Tematy omówione w tym artykule obejmują:

- [Układy menu](#_core_menu_layouts)

- [Paski narzędzi i paski stanu](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Układy menu

Pierwszym krokiem jest koordynowanie układów menu. Aplikacje kontenerów należy utworzyć nowe menu, które ma być używane tylko wtedy, gdy elementy osadzone są aktywowane w miejscu. Co najmniej, to menu powinno składać się z następujących, w kolejności wymienionej:

1. Menu pliku identyczne z menu używanego podczas otwierania plików. (Zazwyczaj żadne inne elementy menu nie są umieszczane przed następnym elementem).

1. Dwa kolejne separatory.

1. Menu okna identyczne z menu używanego, gdy pliki są otwarte (tylko wtedy, gdy aplikacja kontenera w aplikacji MDI). Niektóre aplikacje mogą mieć inne menu, takie jak menu Opcje, które należą do tej grupy, która pozostaje w menu, gdy element osadzony jest aktywowany w miejscu.

    > [!NOTE]
    >  Mogą istnieć inne menu, które wpływają na widok dokumentu kontenera, takie jak Powiększenie. Te menu kontenerów są wyświetlane między dwoma separatorami w tym zasobie menu.

Aplikacje serwerowe (składowe) powinny również utworzyć nowe menu specjalnie do aktywacji w miejscu. Powinno być jak menu używane, gdy pliki są otwarte, ale bez elementów menu, takich jak Plik i Okno, które manipulują dokumentem serwera zamiast danych. Zazwyczaj to menu składa się z następujących elementów:

1. Edytuj menu identyczne z menu używanego, gdy pliki są otwarte.

1. Separator.

1. Menu edycji obiektów, takie jak menu Pióro w przykładowej aplikacji Bazgroły.

1. Separator.

1. Menu Pomocy.

Na przykład spójrz na układ niektórych przykładowych menu w miejscu kontenera i serwera. Szczegóły każdego elementu menu zostały usunięte, aby przykład był bardziej przejrzysty. W menu w miejscu kontenera znajdują się następujące wpisy:

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

Kolejne separatory wskazują, gdzie powinna trafić pierwsza część menu serwera. Teraz spójrz na menu w miejscu serwera:

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

Separatory w tym miejscu wskazują, gdzie druga grupa elementów menu kontenera powinny iść. Wynikowa struktura menu, gdy obiekt z tego serwera jest aktywowany w miejscu wewnątrz tego kontenera wygląda następująco:

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

Jak widać, separatory zostały zastąpione różnymi grupami menu każdej aplikacji.

Tabele akceleratora skojarzone z menu w miejscu powinny być również dostarczane przez aplikację serwera. Kontener będzie zawierać je do własnych tabel akceleratora.

Gdy element osadzony jest aktywowany w miejscu, struktura ładuje menu w miejscu. Następnie prosi aplikację serwera o menu aktywacji w miejscu i wstawia ją tam, gdzie znajdują się separatory. W ten sposób menu łączą się. Otrzymujesz menu z kontenera do pracy w pliku i umieszczeniu okna, a otrzymasz menu z serwera do pracy na elemencie.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Paski narzędzi i paski stanu

Aplikacje serwera powinny utworzyć nowy pasek narzędzi i zapisać jego mapę bitową w oddzielnym pliku. Aplikacje generowane przez kreatora aplikacji przechowują tę mapę bitową w pliku o nazwie ITOOLBAR. Bmp. Nowy pasek narzędzi zastępuje pasek narzędzi aplikacji kontenera, gdy element serwera jest aktywowany na miejscu i powinien zawierać te same elementy, co zwykły pasek narzędzi, ale usuwa ikony reprezentujące elementy w menu Plik i Okno.

Ten pasek narzędzi jest `COleIPFrameWnd`ładowany do klasy pochodnej, utworzonej dla Ciebie przez kreatora aplikacji. Pasek stanu jest obsługiwany przez aplikację kontenera. Aby uzyskać więcej informacji na temat implementacji okien ramek w miejscu, zobacz [Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Aktywacja](../mfc/activation-cpp.md)<br/>
[Serwery](../mfc/servers.md)<br/>
[Containers](../mfc/containers.md)
