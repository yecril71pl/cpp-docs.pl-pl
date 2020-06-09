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
ms.openlocfilehash: a2d3683b744493bb5566456b9e1358c1ddc418d4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615976"
---
# <a name="control-bars"></a>Paski sterowania

"Pasek sterowania" to ogólna nazwa pasków narzędzi, pasków stanu i pasków dialogowych. Klasy MFC `CToolBar` ,,, `CStatusBar` `CDialogBar` `COleResizeBar` i `CReBar` dziedziczyją z klasy [CControlBar](reference/ccontrolbar-class.md), która implementuje ich wspólne funkcje.

Paski sterowania to okna, w których są wyświetlane wiersze formantów, z których użytkownicy mogą wybierać opcje, wykonywać polecenia lub uzyskiwać informacje o programie. Typy pasków sterowania obejmują paski narzędzi, paski okien dialogowych i paski stanu.

- Paski narzędzi w klasie [CToolBar](reference/ctoolbar-class.md)

- Słupki stanu, w klasie [CStatusBar](reference/cstatusbar-class.md)

- Paski okna dialogowego w klasie [CDialogBar](reference/cdialogbar-class.md)

- Paski w klasie [CReBar](reference/crebar-class.md)

> [!IMPORTANT]
> Począwszy od wersji 4,0, paski narzędzi, paski stanu i wskazówki dotyczące narzędzi są implementowane przy użyciu funkcji systemu wdrożonej w *comctl32. dll* zamiast poprzedniej implementacji specyficznej dla MFC. W bibliotece MFC w wersji 6,0, `CReBar` która również otacza funkcję comctl32. dll, została dodana.

Krótkie wprowadzenie do typów pasków kontrolek. Aby uzyskać więcej informacji, zobacz poniższe linki.

## <a name="control-bars"></a>Paski sterowania

Paski sterowania znacznie rozszerzają użyteczność programu, dostarczając szybkie, jednoetapowe akcje poleceń. Klasa `CControlBar` udostępnia typowe funkcje wszystkich pasków narzędzi, pasków stanu i pasków dialogowych. `CControlBar`oferuje funkcje do pozycjonowania paska sterowania w oknie ramki nadrzędnej. Ponieważ pasek sterowania jest zwykle oknem podrzędnym okna ramki nadrzędnej, jest to "równorzędne" do widoku klienta lub klienta MDI okna ramki. Obiekt paska sterowania używa informacji o prostokącie klienta okna nadrzędnego, aby pomieścić siebie. Następnie zmienia pozostały prostokąt okna klienta elementu nadrzędnego, aby widok klienta lub okno klienta MDI wypełnił resztę okna klienta.

> [!NOTE]
> Jeśli przycisk na pasku sterowania nie ma procedury obsługi **polecenia** lub **UPDATE_COMMAND_UI** , struktura automatycznie wyłącza przycisk.

## <a name="toolbars"></a>Paski narzędzi

Pasek narzędzi to pasek sterowania, który wyświetla wiersz przycisków mapy bitowej, które wykonują polecenia. Naciśnięcie przycisku paska narzędzi jest równoznaczne z wybraniem elementu menu; wywołuje tę samą procedurę obsługi zamapowana na element menu, jeśli ten element menu ma ten sam identyfikator jak przycisk paska narzędzi. Przyciski można skonfigurować tak, aby były wyświetlane i zachowywały się jak przyciski radiowe lub pola wyboru. Pasek narzędzi jest zwykle wyrównany do górnej części okna ramki, ale pasek narzędzi MFC może być "Dock" po każdej stronie jego okna nadrzędnego lub zmiennoprzecinkowej w osobnym oknie mini-frame. Pasek narzędzi może być również "float" i można zmienić jego rozmiar i przeciągnąć go za pomocą myszy. Na pasku narzędzi można także wyświetlić wskazówki dotyczące narzędzi, gdy użytkownik przesuwa wskaźnik myszy nad przyciskami paska narzędzi. Etykietka narzędzia to małe okno podręczne, które zwięźle opisuje przeznaczenie przycisku.

> [!NOTE]
> Począwszy od biblioteki MFC w wersji 4,0, Klasa [CToolBar](reference/ctoolbar-class.md) używa typowej kontrolki paska narzędzi systemu Windows. A `CToolBar` zawiera element [CToolBarCtrl](reference/ctoolbarctrl-class.md). Starsze paski narzędzi są jednak nadal obsługiwane. Zobacz [paski narzędzi](mfc-toolbar-implementation.md)artykułów.

## <a name="status-bars"></a>Paski stanu

Pasek stanu jest paskiem sterowania, który zawiera okienka tekstu wyjściowego lub "wskaźniki". Okienka danych wyjściowych są często używane jako wiersze komunikatów i jako wskaźniki stanu. Przykłady wierszy komunikatów zawierają pomoc polecenia — wiersze komunikatów, które krótko objaśniają wybrane menu lub polecenia paska narzędzi w okienku po lewej stronie domyślnego paska stanu utworzonego przez Kreatora aplikacji MFC. Przykłady wskaźników stanu obejmują BLOKADę przewijania, NUM LOCK i inne klucze. Słupki stanu są zazwyczaj wyrównane do dołu okna ramki. Zobacz klasy [CStatusBar](reference/cstatusbar-class.md) i Klasa [CStatusBarCtrl](reference/cstatusbarctrl-class.md).

## <a name="dialog-bars"></a>Paski dialogowe

Pasek okna dialogowego to pasek sterowania oparty na zasobie szablonu okna dialogowego z funkcją niemodalnego okna dialogowego. Paski okna dialogowego mogą zawierać kontrolki Windows, niestandardowe lub ActiveX. Podobnie jak w oknie dialogowym, użytkownik może przełączać się między kontrolkami. Paski okna dialogowego mogą być wyrównane do górnego, dolnego, lewego lub prawego boku okna ramki i mogą być również przepływane w osobnym oknie ramek. Zobacz Klasa [CDialogBar](reference/cdialogbar-class.md).

## <a name="rebars"></a>Paski

[Paska pomocniczego](using-crebarctrl.md) to pasek sterowania, który udostępnia informacje dotyczące dokowania, układu, stanu i trwałości dla formantów paska pomocniczego. Obiekt paska pomocniczego może zawierać różne okna podrzędne, zwykle inne kontrolki, takie jak pola edycji, paski narzędzi i pola listy. Obiekt paska pomocniczego może wyświetlać jego okna podrzędne przez określoną mapę bitową. Rozmiar można zmienić automatycznie lub ręcznie, klikając lub przeciągając jego pasek uchwytu. Zobacz Klasa [CReBar](reference/crebar-class.md).

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)
