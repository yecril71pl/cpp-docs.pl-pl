---
title: Paski sterowania
ms.date: 11/04/2016
helpviewer_keywords:
- command bars [MFC], types of
- toolbars [MFC], control bars
- control bars [MFC]
- MFC, control bars
- control bars [MFC], types of
- CDialogBar class [MFC], control bars
- status bars [MFC], control bars
- CControlBar class [MFC], MFC control bars
- dialog bars [MFC], control bars
- CToolBar class [MFC], control bars
- CStatusBar class [MFC], control bars
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
ms.openlocfilehash: 4b75d9a96f091d0424592f34bdb1ed7ce76c2372
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283582"
---
# <a name="control-bars"></a>Paski sterowania

"Pasek sterowania" jest ogólna nazwa dla pasków narzędzi, paski stanu i paski dialogowe. Klasy MFC `CToolBar`, `CStatusBar`, `CDialogBar`, `COleResizeBar`, i `CReBar` pochodzi od klasy [CControlBar](../mfc/reference/ccontrolbar-class.md), który implementuje ich typowych funkcji.

Paski sterowania są, wyświetlające wierszy kontrolki za pomocą których użytkowników można wybrać opcje, wykonaj polecenia lub uzyskiwanie informacji o programie. Paski sterowania należą paski narzędzi, paski dialogowe i stanu.

- Paski narzędzi w klasie [CToolBar](../mfc/reference/ctoolbar-class.md)

- Paski stanu, w klasie [CStatusBar](../mfc/reference/cstatusbar-class.md)

- Paski dialogowe, w klasie [CDialogBar](../mfc/reference/cdialogbar-class.md)

- Rebars w klasie [CReBar](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
>  MFC w wersji 4.0, paski narzędzi, paski stanu i narzędzia wskazówki są implementowane za pomocą funkcji systemu zaimplementowane w *comctl32.dll* zamiast poprzedniej implementacji MFC. W wersji 6.0, MFC `CReBar`, funkcje comctl32.dll, która opakowuje również został dodany.

Wykonaj krótkie wprowadzenia do typów paska sterowania. Aby uzyskać więcej informacji zobacz poniższe linki.

## <a name="control-bars"></a>Paski sterowania

Paski sterowania znacznie zwiększyć użyteczność program, zapewniając szybki i akcje poleceń jednoetapowy. Klasa `CControlBar` zawiera typowe funkcje wszystkich pasków narzędzi, paski stanu i paski dialogowe. `CControlBar` oferuje funkcje dla strony paska sterowania jej nadrzędnej ramki okna. Pasek sterowania to zazwyczaj okno podrzędne dla nadrzędnej ramki okna, dlatego jest elementem równorzędnym "węzła" do widoku klienta lub klienta MDI ramki okna. Obiekt paska sterowania używa informacji dotyczących prostokąta klienta okna nadrzędnego do samej pozycji. A następnie zmienia pozostałe prostokąt klienta okna nadrzędnego, tak aby widoku klienta lub okno klienckie MDI wypełnia pozostałe okna klienta.

> [!NOTE]
>  Jeśli nie ma przycisku na pasku sterowania **polecenia** lub **UPDATE_COMMAND_UI** obsługi w ramach automatycznie wyłącza przycisk.

## <a name="toolbars"></a>Paski narzędzi

Pasek narzędzi jest pasek sterowania, który wyświetla wiersz przycisków mapy bitowej, który wykonywać polecenia. Jest równoważne wybraniu elementu menu; naciśnięcie przycisku paska narzędzi wywołuje program obsługi tego samego mapowany na element menu, jeśli ten element menu ma taki sam identyfikator jak przycisk na pasku narzędzi. Można skonfigurować przyciski są wyświetlane i zachowują się jak przyciski, przyciski radiowe i pola wyboru. Pasek narzędzi jest zazwyczaj wyrównane do górnej części okna ramki, ale narzędzi MFC można "zadokować" boku jego okno nadrzędne lub float w osobnym oknie mini ramki. Pasek narzędzi można również "float" i możesz zmienić jego rozmiar i przeciągnij go za pomocą myszy. Pasek narzędzi można także wyświetlać etykietek narzędzi, gdy użytkownik przesuwa mysz przycisku paska. Etykietka narzędzia jest bardzo mały wyskakujące, stanowiącą zwięzły opis przeznaczenia przycisku.

> [!NOTE]
>  Począwszy od wersji 4.0 MFC, klasa [CToolBar](../mfc/reference/ctoolbar-class.md) używa formantu typowego paska narzędzi Windows. A `CToolBar` zawiera [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Starsze paski narzędzi są nadal obsługiwane, ale. Zapoznaj się z artykułem [pasków narzędzi](../mfc/mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Paski stanu

Pasek stanu jest pasek sterowania, który zawiera tekstu wyjściowego okienka lub "wskaźniki." Okienka danych wyjściowych są często używane jako wiersz wiadomości, a wskaźniki stanu. Komunikat wiersza Przykładami wierszy komunikat pomocy polecenia krótko opisano wybranego menu lub paska narzędzi, polecenia skrajnie po lewej stronie okienka paska stanu domyślne, które są tworzone przez Kreatora aplikacji MFC. Stan wskaźnika przykładami innych kluczy, SCROLL LOCK i NUM LOCK. Paski stanu są zazwyczaj wyrównane do dolnej części okna ramki. Można znaleźć klasy [CStatusBar](../mfc/reference/cstatusbar-class.md) i klasa [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Paski dialogowe

Pasek dialogowy jest pasek sterowania, oparty na zasobu szablonu okna dialogowego, funkcje niemodalnego okna dialogowego. Paski dialogowe może zawierać Windows, niestandardowych lub formantów ActiveX. Jak okno dialogowe użytkownik może karta między formantami. Paski dialogowe może być wyrównane do górnej, dolnej, lewej lub po prawej stronie okna ramki i mogą być również przestawione w ich własnych ramki okna. Można znaleźć klasy [CDialogBar](../mfc/reference/cdialogbar-class.md).

## <a name="rebars"></a>Rebars

A [paska pomocniczego](../mfc/using-crebarctrl.md) jest pasek sterowania, który zawiera informacje o dokowania, układ, stanu i trwałości dla formantów rebar. Obiekt paska pomocniczego może zawierać wiele okien podrzędnych, zazwyczaj inne kontrolki, w tym pola tekstowe, paski narzędzi i pól listy. Obiekt paska pomocniczego, można wyświetlić jego okien podrzędnych za pośrednictwem określonego mapy bitowej. Jego można automatycznie lub ręcznie zmienić rozmiar, klikając lub przeciągnij jej pasek uchwytu. Można znaleźć klasy [CReBar](../mfc/reference/crebar-class.md).

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
