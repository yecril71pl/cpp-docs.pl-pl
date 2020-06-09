---
title: Elementy interfejsu
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: 4d4d81287cb30a7d3608025085cdb3f9a208147a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619991"
---
# <a name="interface-elements"></a>Elementy interfejsu

W tym dokumencie opisano elementy interfejsu, które zostały wprowadzone w programie Visual Studio 2008 z dodatkiem SP1, a także opisano różnice w poprzedniej wersji biblioteki.

Na poniższej ilustracji przedstawiono aplikację, która została skompilowana przy użyciu nowych elementów interfejsu.

![Przykładowa aplikacja pakietu MFC Feature Pack](../mfc/media/mfc_featurepack.png "Przykładowa aplikacja pakietu MFC Feature Pack")

## <a name="window-docking"></a>Dokowanie okna

Funkcja dokowania okna przypomina dokowanie okna, które jest używane przez graficzny interfejs użytkownika programu Visual Studio.

## <a name="control-bars-are-now-panes"></a>Paski sterowania są teraz okienkami

Paski sterowania są teraz nazywane okienkami i pochodzą z [klasy CBasePane](reference/cbasepane-class.md). We wcześniejszych wersjach MFC były klasą bazową pasków sterowania `CControlBar` .

Okno głównej ramki aplikacji jest zwykle reprezentowane przez [klasę CFrameWndEx](reference/cframewndex-class.md) lub [klasę CMDIFrameWndEx](reference/cmdiframewndex-class.md). Główna ramka jest nazywana *lokacją Dock*. Okienka mogą mieć jeden z trzech typów obiektów nadrzędnych: witrynę Dock, pasek dokowania lub okno mini-frame.

Istnieją dwa typy okienek: bez zmiany rozmiaru i zmienny rozmiar. Można zmienić rozmiar okienek o zmiennym rozmiarze, takich jak paski stanu i paski narzędzi, przy użyciu rozdzielaczy lub suwaków. Okienka o zmiennym rozmiarze mogą tworzyć kontenery (jedno okienko można zadokować w innym okienku, tworząc rozdzielacz między nimi). Jednak okienka o zmiennym rozmiarze nie mogą być dołączane (zadokowane) do słupków dokowania.

Jeśli aplikacja używa okienek bez zmiany rozmiaru, utwórz je z [klasy CPane](reference/cpane-class.md).  Jeśli aplikacja używa okienek o zmiennym rozmiarze, utwórz je z [klasy CDockablePane](reference/cdockablepane-class.md)

## <a name="dock-site"></a>Witryna Docker

Witryna Docker (lub okno ramki głównej) jest właścicielem wszystkich okienek oraz okienek z ramkami w aplikacji. Witryna Docker zawiera element członkowski [CDockingManager](reference/cdockingmanager-class.md) . Ten element członkowski zachowuje listę wszystkich okienek, które należą do witryny Docker. Lista jest uporządkowana w taki sposób, aby okienka utworzone na zewnętrznych krawędziach witryny Dock zostały umieszczone na początku listy. Gdy struktura ponownie narysuje lokację Dock, przetworzy pętlę na tej liście i dostosowuje układ każdego okienka, aby uwzględnić bieżący prostokąt związany z witryną Docker. Można wywołać `AdjustDockingLayout` lub `RecalcLayout` w przypadku konieczności dostosowania układu dokowania, a platforma przekierowuje to wywołanie do Menedżera dokowania.

## <a name="dock-bars"></a>Słupki dokowania

Każde okno głównej ramki może umieścić na nim *paski dokowania* . Pasek dokowania jest okienkiem, które należy do [klasy CDockSite](reference/cdocksite-class.md). Paski dokowania mogą akceptować obiekty pochodne od [CPane](reference/cpane-class.md), takie jak paski narzędzi. Aby utworzyć paski dokowania po zainicjowaniu okna głównego ramki, wywołaj `EnableDocking` . Aby włączyć Autoukrywanie pasków, wywołaj `EnableAutoHideBars` . `EnableAutoHideBars`tworzy obiekty [CAutoHideDockSite](reference/cautohidedocksite-class.md) i umieszcza je obok każdego paska dokowania.

Każdy słupek dokowania jest podzielony na wiersze dokowania. Wiersze dokowania są reprezentowane przez [klasę CDockingPanesRow](reference/cdockingpanesrow-class.md). Każdy wiersz dokowania zawiera listę pasków narzędzi. Jeśli użytkownik zadokuje pasek narzędzi lub przenosi pasek narzędzi z jednego wiersza do drugiego w obrębie tego samego paska dokowania, struktura utworzy nowy wiersz i zmienia rozmiar paska dokowania odpowiednio lub umieszcza pasek narzędzi w istniejącym wierszu.

## <a name="mini-frame-windows"></a>Okna mini-frame

Okienko przestawne znajduje się w oknie mini-frame. Okna mini-frame są reprezentowane przez dwie klasy: [Klasa CMDITabInfo](reference/cmditabinfo-class.md) (która może zawierać tylko jedno okienko) i [Klasa CMultiPaneFrameWnd](reference/cmultipaneframewnd-class.md) (które mogą zawierać kilka okienek). Aby przestawić okienko w kodzie, zadzwoń do [CBasePane:: FloatPane](reference/cbasepane-class.md#floatpane). Po przejściu w okienku struktura automatycznie tworzy okno mini-frame i że okno mini-frame zostanie przepływające względem nadrzędnego okienka. Gdy okienko przestawne zostanie zadokowane, struktura resetuje swój element nadrzędny, a okienko przestawne przejdzie do paska dokowania (dla pasków narzędzi) lub dla witryny Dock (dla okienek o zmiennym rozmiarze).

## <a name="pane-dividers"></a>Separatory okienka

Podziały okienka (również nazwane suwaki lub rozdzielacze) są reprezentowane przez [klasę CPaneDivider](reference/cpanedivider-class.md). Gdy użytkownik zadokuje okienko, struktura tworzy dzielniki okienka, niezależnie od tego, czy okienko jest zadokowane w witrynie Dock lub w innym okienku. Gdy okienko zostanie zadokowane w witrynie Docker, dzielnik okienka jest nazywany *domyślnym separatorem okienka*. Domyślny podział okienka jest odpowiedzialny za układ wszystkich okienek dokowania w witrynie Docker. Menedżer Docker utrzymuje listę domyślnych podziałów okien i listę okienek. Menedżery dokowania są odpowiedzialne za układ wszystkich okienek dokowania.

## <a name="containers"></a>Containers

Wszystkie okienka o zmiennym rozmiarze, gdy są zadokowane do siebie, są utrzymywane w kontenerach. Kontenery są reprezentowane przez [klasę CPaneContainer](reference/cpanecontainer-class.md). Każdy kontener ma wskaźniki do lewego okienka, prawego okienka, lewego kontenera podrzędnego, podkontenera praw i rozdzielacza między częścią lewą i prawą. (*Lewe* i *prawe* nie odnoszą się do fizycznych stron, ale zamiast identyfikować gałęzie struktury drzewa). W ten sposób możemy skompilować drzewo okienek i rozdzielaczy, a tym samym uzyskać złożone układy okienek, które mogą być zmieniane razem. `CPaneContainer`Klasa utrzymuje drzewo kontenerów, a także utrzymuje dwie listy okienek i suwaków, które znajdują się w tym drzewie. Menedżerowie kontenerów okienka są zwykle osadzani w domyślnych suwakach i oknach z ramkami mini, które zawierają wiele okienek.

## <a name="auto-hide-control-bars"></a>Autoukrywanie pasków sterowania

Domyślnie każda z nich `CDockablePane` obsługuje funkcję Autoukrywanie. Gdy użytkownik kliknie przycisk pinezki w podpisie `CDockablePane` , struktura przełączy okienko w tryb autoukrywania. Aby obsłużyć kliknięcia, struktura tworzy [klasę CMFCAutoHideBar](reference/cmfcautohidebar-class.md) i [klasę CMFCAutoHideButton](reference/cmfcautohidebutton-class.md) skojarzoną z `CMFCAutoHideBar` obiektem. Struktura umieszcza nowy `CMFCAutoHideBar` na [CAutoHideDockSite](reference/cautohidedocksite-class.md). Struktura dołącza również `CMFCAutoHideButton` do paska narzędzi. [Klasa CDockingManager](reference/cdockingmanager-class.md) obsługuje `CDockablePane` .

## <a name="tabbed-control-bars-and-outlook-bars"></a>Paski kontroli z kartami i paski programu Outlook

[Klasa CMFCBaseTabCtrl](reference/cmfcbasetabctrl-class.md) implementuje podstawowe funkcje okna z kartami z kartami do odłączenia. Aby użyć `CMFCBaseTabCtrl` obiektu, zainicjuj [klasę CBaseTabbedPane](reference/cbasetabbedpane-class.md) w aplikacji. `CBaseTabbedPane`pochodzi od `CDockablePane` i utrzymuje wskaźnik do `CMFCBaseTabCtrl` obiektu. `CBaseTabbedPane`Umożliwia użytkownikom dokowanie i zmienianie rozmiaru pasków sterowania z kartami. Użyj [CDockablePane:: AttachToTabWnd](reference/cdockablepane-class.md#attachtotabwnd) , aby dynamicznie utworzyć paski sterowania, które są zadokowane i z zakładkami.

Kontrolka pasek programu Outlook jest również oparta na paskach kart. [Klasa CMFCOutlookBar](reference/cmfcoutlookbar-class.md) jest pochodną klasy `CBaseTabbedPane` . Aby uzyskać więcej informacji na temat korzystania z paska Outlook, zobacz [CMFCOutlookBar Class](reference/cmfcoutlookbar-class.md).

## <a name="see-also"></a>Zobacz też

[Pojęcia](mfc-concepts.md)
