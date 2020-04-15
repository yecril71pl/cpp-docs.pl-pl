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
ms.openlocfilehash: ceae20c89d9a6d3f4393f838b3594938107785f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353569"
---
# <a name="control-bars"></a>Paski sterowania

"Pasek sterowania" to ogólna nazwa pasków narzędzi, pasków stanu i pasków dialogowych. Klasy `CToolBar`MFC `CStatusBar` `CDialogBar`, `COleResizeBar`, `CReBar` i pochodzą z klasy [CControlBar](../mfc/reference/ccontrolbar-class.md), który implementuje ich wspólne funkcje.

Paski sterowania to okna, które wyświetlają wiersze formantów, za pomocą których użytkownicy mogą wybierać opcje, wykonywać polecenia lub uzyskiwać informacje o programie. Typy pasków sterowania obejmują paski narzędzi, paski dialogowe i paski stanu.

- Paski narzędzi, w klasie [CToolBar](../mfc/reference/ctoolbar-class.md)

- Paski stanu, w klasie [CStatusBar](../mfc/reference/cstatusbar-class.md)

- Paski okiennia, w klasie [CDialogBar](../mfc/reference/cdialogbar-class.md)

- Pręty zbrojeniowe klasy [CReBar](../mfc/reference/crebar-class.md)

> [!IMPORTANT]
> Od wersji MFC 4.0 paski narzędzi, paski stanu i porady dotyczące narzędzi są implementowane przy użyciu funkcji systemu zaimplementowanych w *pliku comctl32.dll* zamiast poprzedniej implementacji specyficznej dla MFC. W wersji MFC 6.0, `CReBar`który również zawija funkcje comctl32.dll, został dodany.

Krótkie wprowadzenie do typów paska sterowania następują. Aby uzyskać więcej informacji, zobacz poniższe linki.

## <a name="control-bars"></a>Paski sterowania

Paski sterowania znacznie zwiększają użyteczność programu, zapewniając szybkie, jednoetapowe akcje poleceń. Klasa `CControlBar` zapewnia wspólne funkcje wszystkich pasków narzędzi, pasków stanu i pasków dialogowych. `CControlBar`zapewnia funkcje pozycjonowania paska sterowania w oknie ramki nadrzędnej. Ponieważ pasek sterowania jest zwykle okno podrzędne okna ramki nadrzędnej, jest "elementem równorzędnym" do widoku klienta lub klienta MDI okna ramki. Obiekt paska sterowania używa informacji o jego prostokąt klienta okna nadrzędnego do położenia się. Następnie zmienia prostokąt pozostałych okna klienta nadrzędnego, tak aby widok klienta lub okno klienta MDI wypełnia pozostałą część okna klienta.

> [!NOTE]
> Jeśli przycisk na pasku sterowania nie ma **polecenia** lub **UPDATE_COMMAND_UI** obsługi, struktura automatycznie wyłącza przycisk.

## <a name="toolbars"></a>Paski narzędzi

Pasek narzędzi to pasek sterowania, który wyświetla wiersz przycisków bitmapowych, które wykonują polecenia. Naciśnięcie przycisku paska narzędzi jest równoznaczne z wybraniem elementu menu; wywołuje ten sam program obsługi mapowany do elementu menu, jeśli ten element menu ma ten sam identyfikator co przycisk paska narzędzi. Przyciski można skonfigurować tak, aby były wyświetlane i zachowywały się jak przyciski, przyciski radiowe lub pola wyboru. Pasek narzędzi jest zwykle wyrównany do górnej części okna ramki, ale pasek narzędzi MFC może "dokować" do dowolnej strony okna nadrzędnego lub unosić się w swoim własnym oknie mini-ramki. Pasek narzędzi może również "float" i można zmienić jego rozmiar i przeciągnąć go za pomocą myszy. Pasek narzędzi może również wyświetlać wskazówki dotyczące narzędzi, gdy użytkownik przesuwa kursor myszy nad przyciskami paska narzędzi. Etykietka narzędzia to małe okno podręczne, które pokrótce opisuje cel przycisku.

> [!NOTE]
> W wersji MFC 4.0, klasa [CToolBar](../mfc/reference/ctoolbar-class.md) używa wspólnego formantu paska narzędzi systemu Windows. A `CToolBar` zawiera [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md). Starsze paski narzędzi są jednak nadal obsługiwane. Zobacz artykuł [Paski narzędziowe](../mfc/mfc-toolbar-implementation.md).

## <a name="status-bars"></a>Paski stanu

Pasek stanu to pasek sterowania zawierający okienka tekstowo-wyjściowe lub "wskaźniki". Okienka danych wyjściowych są powszechnie używane jako linie komunikatów i jako wskaźniki stanu. Przykłady wierszy komunikatów obejmują wiersze pomocy polecenia, które krótko wyjaśniają wybrane menu lub polecenie paska narzędzi w lewym okienku domyślnego paska stanu utworzonego przez Kreatora aplikacji MFC. Przykłady wskaźników stanu obejmują SCROLL LOCK, NUM LOCK i inne klucze. Paski stanu są zwykle wyrównane do dolnej części okna ramki. Zobacz klasę [CStatusBar](../mfc/reference/cstatusbar-class.md) i klasę [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Paski dialogowe

Pasek dialogowy to pasek sterowania oparty na zasobie szablonu okna dialogowego z funkcją niemodytowego okna dialogowego. Paski dialogowe mogą zawierać formanty systemu Windows, niestandardowe lub ActiveX. Podobnie jak w oknie dialogowym, użytkownik może tabulator wśród formantów. Paski dialogowe można wyrównać do górnej, dolnej, lewej lub prawej strony okna ramki i mogą być również unoszone we własnym oknie ramki. Zobacz klasę [CDialogBar](../mfc/reference/cdialogbar-class.md).

## <a name="rebars"></a>Pręty zbrojeniowe

Pręt [zbrojeniowy](../mfc/using-crebarctrl.md) to pasek sterowania, który zapewnia informacje o dokowaniu, układzie, stanie i trwałości dla formantów prętów zbrojeniowych. Obiekt prętów zbrojeniowych może zawierać różne okna podrzędne, zazwyczaj inne formanty, w tym pola edycji, paski narzędzi i pola listy. Obiekt prętów zbrojeniowych może wyświetlać swoje okna podrzędne na określonej mapie bitowej. Można go automatycznie lub ręcznie zmielidzić, klikając lub przeciągając pasek chwytaka. Zobacz klasę [CReBar](../mfc/reference/crebar-class.md).

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
