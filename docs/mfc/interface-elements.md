---
title: Elementy interfejsu
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: fa6dc78c95717f9201e18346f1cbe573fa3c48d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153584"
---
# <a name="interface-elements"></a>Elementy interfejsu

W tym dokumencie opisano elementy interfejsu, które zostały wprowadzone w programie Visual Studio 2008 z dodatkiem SP1, a także w tym artykule opisano różnice za pomocą wcześniejszej wersji biblioteki.

Na poniższej ilustracji przedstawiono aplikację, która została skompilowana przy użyciu nowych elementów interfejsu.

![MFC Feature Pack Przykładowa aplikacja](../mfc/media/mfc_featurepack.png "MFC Feature Pack przykładowej aplikacji")

## <a name="window-docking"></a>Dokowanie okien

Funkcje dokowania okna przypomina okna dokowania, że korzysta z programu Visual Studio graficznego interfejsu użytkownika.

## <a name="control-bars-are-now-panes"></a>Paski sterowania to teraz okienek

Paski sterowania są teraz znane jako okienkami i są uzyskiwane z [klasa CBasePane](../mfc/reference/cbasepane-class.md). We wcześniejszych wersjach programu MFC, klasa bazowa paski sterowania był `CControlBar`.

W oknie głównym ramki aplikacji jest zwykle reprezentowany przez [klasa CFrameWndEx](../mfc/reference/cframewndex-class.md) lub [klasa CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md). Nosi nazwę głównej ramki *zadokować witryny*. Okienka może mieć jeden z trzech typów elementów nadrzędnych: witrynie stacji dokującej, na pasku dokowania lub okna mini ramki.

Istnieją dwa typy okienka: bez o zmiennym rozmiarze i o zmiennym rozmiarze. Można zmienić rozmiar okienka o zmiennym rozmiarze, takie jak paski stanu i paski narzędzi, za pomocą rozdzielaczy lub suwaki. Zmienny rozmiar okienka można tworzyć kontenery (jedno okienko może być zadokowane do okienka innego, Tworzenie podziału między nimi). Jednak o zmiennym rozmiarze okienka nie można dołączyć (zadokowany), aby zadokować pasków.

Jeśli aplikacja korzysta z innych o zmiennym rozmiarze okienka, pochodzi od [klasa CPane](../mfc/reference/cpane-class.md).  Jeśli aplikacja korzysta z możliwością zmiany rozmiaru okienka, pochodzi od [klasa CDockablePane](../mfc/reference/cdockablepane-class.md)

## <a name="dock-site"></a>Witryny dokowania

Witryny dokowania (lub ramką głównego okna) jest właścicielem wszystkich okienek i okien mini ramki w aplikacji. Zawiera witryny dokowania [CDockingManager](../mfc/reference/cdockingmanager-class.md) elementu członkowskiego. Ten element członkowski przechowuje listę wszystkich okienek, które należą do witryny dokowania. Lista jest uporządkowana, tak aby okienka utworzono zewnętrznej krawędzi witryny dokowania są umieszczone na początku listy. Gdy w ramach odrysowuje witryny dokowania, za pośrednictwem tej listy w pętli i dostosowuje układ każde okienko, aby uwzględnić bieżący prostokąt otaczający witryny dokowania. Możesz wywołać `AdjustDockingLayout` lub `RecalcLayout` gdy trzeba dostosować układ dokowania, a struktura przekierowuje to wywołanie Menedżera dokowania.

## <a name="dock-bars"></a>Paski dokowania

Każde okno ramki głównej można umieścić *dokowania pasków* wzdłuż jego krawędzi. Na pasku dokowania to okienko, który należy do [klasa CDockSite](../mfc/reference/cdocksite-class.md). Dokowania pasków może akceptować obiekty opracowane na podstawie [CPane](../mfc/reference/cpane-class.md), takich jak pasków narzędzi. Aby utworzyć dokowania pasków po zainicjowaniu ramką głównego okna, wywołaj `EnableDocking`. Aby włączyć automatyczne ukrywanie paski, należy wywołać `EnableAutoHideBars`. `EnableAutoHideBars` Tworzy [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md) obiektów i umieszcza je obok każdego pasek dokowania.

Każdy słupek dock jest podzielony na wiersze dokowania. Zadokuj wiersze są reprezentowane przez [klasa CDockingPanesRow](../mfc/reference/cdockingpanesrow-class.md). Każdy wiersz dock zawiera lista pasków narzędzi. Jeśli użytkownik dokowane paska narzędzi lub przenosi pasek narzędzi z jednego wiersza do innego w taki sam pasek dokowania, ramach tworzy nowy wiersz i w związku z tym zmienia rozmiar na pasku dokowania lub Ustawia położenie paska narzędzi na istniejący wiersz.

## <a name="mini-frame-windows"></a>Windows mini ramki

Okienko przestawne znajduje się w okno mini ramki. Windows mini ramki są reprezentowane przez dwie klasy: [Klasa CMDITabInfo](../mfc/reference/cmditabinfo-class.md) (która może zawierać tylko jedno okienko) i [klasa CMultiPaneFrameWnd](../mfc/reference/cmultipaneframewnd-class.md) (która może zawierać kilku okienek). Aby przestawić Panel w kodzie, wywołania [CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane). Po pojawia się okienko framework automatycznie tworzy okno mini ramki, a okno mini ramki zostanie okienko przestawne nadrzędnej. Po dokowane okienko przestawne, struktura resetuje jego elementu nadrzędnego i okienko przestawne staje się na pasku dokowania (dla pasków narzędzi) lub (w przypadku o zmiennym rozmiarze okienka) witryny dokowania.

## <a name="pane-dividers"></a>Separator okienka

Separator okienka (zwaną również suwaków lub rozdzielaczy) są reprezentowane przez [klasa CPaneDivider](../mfc/reference/cpanedivider-class.md). Gdy użytkownik dokowane okienko, szablon tworzy separator okienka, niezależnie od tego, czy okienko jest zadokowany w lokacji dokowania lub w innym okienko. Okienko jest dokowane witryny dokowania, separator okienka jest nazywany *domyślne dzielnik*. Separator okienka domyślny jest odpowiedzialny za układ okienek dokowania w witryny dokowania. Menedżer dokowania utrzymuje listę separator okienka domyślne i listą okienek. Menedżerowie dokowania są odpowiedzialne za układ tafli dokowania.

## <a name="containers"></a>Kontenery

Wszystkie o zmiennym rozmiarze okienka, gdy jest zadokowany do siebie, są obsługiwane w kontenerach. Kontenery są reprezentowane przez [klasa CPaneContainer](../mfc/reference/cpanecontainer-class.md). Każdy kontener ma wskaźniki do jej w okienku po lewej stronie, okienku po prawej stronie, po lewej stronie kontenerze podrzędnym, odpowiednim kontenerze podrzędnych i rozdzielacza między częściami po lewej i prawej stronie. (*Po lewej stronie* i *prawo* odwołuje się do strony fizycznej, ale raczej zidentyfikować gałęzie strukturę drzewa.) W ten sposób możemy drzewa okienka i rozdzielaczy kompilacji i w związku z tym uzyskania złożonych układów okienkami, których rozmiar można zmieniać ze sobą. `CPaneContainer` Klasa przechowuje drzewo kontenerów; również obsługuje dwie listy okienka oraz suwaki, które znajdują się w tym drzewie. Okienko kontenera menedżerów zwykle są osadzone w domyślnej suwaki i okna mini ramki, które zawierają wiele okienek.

## <a name="auto-hide-control-bars"></a>Paski sterowania autoukrywanie

Domyślnie każdy `CDockablePane` obsługuje funkcję automatycznego ukrywania. Kiedy użytkownik kliknie przycisk szpilki na podpisie `CDockablePane`, struktura zmienia okienka na trybie autoukrywania. Aby obsłużyć kliknięcie, szablon tworzy [klasa CMFCAutoHideBar](../mfc/reference/cmfcautohidebar-class.md) i [klasa CMFCAutoHideButton](../mfc/reference/cmfcautohidebutton-class.md) skojarzony `CMFCAutoHideBar` obiektu. Struktura umieszcza nowe `CMFCAutoHideBar` na [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md). Dołącza również w ramach `CMFCAutoHideButton` do paska narzędzi. [Klasa CDockingManager](../mfc/reference/cdockingmanager-class.md) przechowuje `CDockablePane`.

## <a name="tabbed-control-bars-and-outlook-bars"></a>Paski sterowania z kartami i paski programu Outlook

[Klasa CMFCBaseTabCtrl](../mfc/reference/cmfcbasetabctrl-class.md) implementuje podstawowe funkcje okna z zakładkami z odłączanymi zakładkami. Aby użyć `CMFCBaseTabCtrl` obiektu, zainicjować [klasa CBaseTabbedPane](../mfc/reference/cbasetabbedpane-class.md) w aplikacji. `CBaseTabbedPane` jest tworzony na podstawie `CDockablePane` i przechowuje wskaźnik do `CMFCBaseTabCtrl` obiektu. `CBaseTabbedPane` Umożliwia użytkownikowi zadokować i zmienianie rozmiaru pasków sterowania z kartami. Użyj [CDockablePane::AttachToTabWnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd) umożliwia dynamiczne tworzenie paski kontroli, które są zadokowane, a z zakładkami.

Kontrolki paska również opiera się na paskach z kartami. [Klasa CMFCOutlookBar](../mfc/reference/cmfcoutlookbar-class.md) jest tworzony na podstawie `CBaseTabbedPane`. Aby uzyskać więcej informacji o sposobie używania pasek programu Outlook, zobacz [klasa CMFCOutlookBar](../mfc/reference/cmfcoutlookbar-class.md).

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)
