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
ms.openlocfilehash: 03d27443f90634b5d787eee25acc951d24178f42
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626225"
---
# <a name="menus-and-resources-menu-merging"></a>Menu i zasoby: scalanie menu

W tym artykule szczegółowo opisano kroki niezbędne do poprawnego obsługi edycji wizualnej i aktywacji w miejscu. Aktywacja w miejscu stanowi wyzwanie dla aplikacji kontenera i serwera (składnika). Użytkownik pozostaje w tym samym oknie ramek (w kontekście dokumentu kontenera), ale w rzeczywistości działa inna aplikacja (serwer). Wymaga to koordynacji między zasobami aplikacji kontenera i serwera.

Tematy omówione w tym artykule obejmują:

- [Układy menu](#_core_menu_layouts)

- [Paski narzędzi i paski stanu](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Układy menu

Pierwszym krokiem jest koordynowanie układów menu. Aplikacje kontenerów powinny tworzyć nowe menu, które mają być używane tylko po aktywowaniu elementów osadzonych. Co najmniej, to menu powinno zawierać następujące elementy w podanej kolejności:

1. Menu plik identyczne z tym, który jest używany, gdy pliki są otwarte. (Zazwyczaj żadne inne elementy menu nie są umieszczane przed następnym elementem).

1. Dwa kolejne separatory.

1. Menu okno identyczne z tą, która jest używana podczas otwierania plików (tylko wtedy, gdy aplikacja kontenera jest w aplikacji MDI). Niektóre aplikacje mogą mieć inne menu, takie jak menu opcji, które należą do tej grupy, która pozostanie w menu po aktywowaniu elementu osadzonego.

    > [!NOTE]
    >  Mogą istnieć inne menu, które mają wpływ na widok dokumentu kontenera, takie jak powiększenie. Te menu kontenerów pojawiają się między dwoma separatorami w tym zasobie menu.

Aplikacje serwera (składników) powinny również utworzyć nowe menu przeznaczone do aktywacji w miejscu. Powinien on przypominać menu używane, gdy pliki są otwarte, ale bez elementów menu, takich jak pliki i okna, które manipulują dokumentem serwera zamiast danych. Zwykle to menu składa się z następujących elementów:

1. Edytuj menu identyczne z tymi, które są używane podczas otwierania plików.

1. Rozdzielając.

1. Menu edycji obiektów, takie jak menu pióro w przykładowej aplikacji Bazgrołowej.

1. Rozdzielając.

1. Menu Pomoc.

Na przykład zapoznaj się z układem niektórych przykładowych menu dla kontenera i serwera. Szczegóły każdego elementu menu zostały usunięte, aby przykład był wyraźniejszy. Menu w miejscu kontenera zawiera następujące wpisy:

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

Kolejne separatory wskazują, gdzie pierwsza część menu serwera powinna się przechodzić. Teraz spójrz na menu w miejscu serwera:

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

W tym miejscu separatory wskazują, gdzie powinna zostać przestawiona druga grupa elementów menu kontenerów. Wynikowa struktura menu, gdy obiekt z tego serwera jest aktywowany w miejscu wewnątrz tego kontenera wygląda następująco:

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

Jak widać, separatory zostały zastąpione różnymi grupami menu poszczególnych aplikacji.

Tabele akceleratorów skojarzone z menu w miejscu powinny być również dostarczane przez aplikację serwera. Kontener dołączy je do własnych tabel akceleratorów.

Gdy element osadzony jest aktywowany na miejscu, struktura ładuje menu w miejscu. Następnie pyta do aplikacji serwera dla aktywacji w miejscu i wstawia ją w miejscu, gdzie separatory są. Jest to sposób łączenia menu. Uzyskasz dostęp do menu z kontenera na potrzeby obsługi plików i umieszczania okna, a następnie uzyskasz menu z serwera na potrzeby obsługi tego elementu.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Paski narzędzi i paski stanu

Aplikacje serwera powinny utworzyć nowy pasek narzędzi i przechowywać jego mapę bitową w osobnym pliku. Aplikacje generowane przez Kreatora aplikacji przechowują tę mapę bitową w pliku o nazwie ITOOLBAR. BMP. Nowy pasek narzędzi zastępuje pasek narzędzi aplikacji kontenera, gdy jest aktywowany element serwera i powinien zawierać te same elementy co normalny pasek narzędzi, ale Usuń ikony reprezentujące elementy w menu plik i okno.

Ten pasek narzędzi jest ładowany w `COleIPFrameWnd` klasie pochodnej utworzonej przez Kreatora aplikacji. Pasek stanu jest obsługiwany przez aplikację kontenera. Aby uzyskać więcej informacji na temat implementacji okien ramowych w miejscu, zobacz [serwery: implementowanie serwera](servers-implementing-a-server.md).

## <a name="see-also"></a>Zobacz też

[Menu i zasoby (OLE)](menus-and-resources-ole.md)<br/>
[Uaktywnienie](activation-cpp.md)<br/>
[Serwery](servers.md)<br/>
[Containers](containers.md)
