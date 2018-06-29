---
title: Elementy interfejsu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1906505e75273cc62a0eac55e6ed1a9686a3b76f
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078447"
---
# <a name="interface-elements"></a>Elementy interfejsu
Ten dokument zawiera opis elementów interfejsu, które zostały wprowadzone w programie Visual Studio 2008 z dodatkiem SP1 i opisano również w przypadku wcześniejszych wersji biblioteki.  
  
 Na poniższej ilustracji przedstawiono aplikację, która została skompilowana przy użyciu nowych elementów interfejsu.  
  
 ![Pakiet funkcji MFC Przykładowa aplikacja](../mfc/media/mfc_featurepack.png "mfc_featurepack")  
  
## <a name="window-docking"></a>Dokowanie okien  
 Okno dokowanie funkcji podobny okna dokowania, który [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] korzysta z graficznego interfejsu użytkownika.  
  
## <a name="control-bars-are-now-panes"></a>Paski sterowania są teraz okienka  
 Paski sterowania są teraz nazywane okienka i pochodne [CBasePane klasy](../mfc/reference/cbasepane-class.md). We wcześniejszych wersjach MFC został klasę podstawową klasy pasków sterowania `CControlBar`.  
  
 W oknie ramki głównej aplikacji jest reprezentowany przez [klasy CFrameWndEx](../mfc/reference/cframewndex-class.md) lub [CMDIFrameWndEx klasy](../mfc/reference/cmdiframewndex-class.md). Ramki głównej jest nazywany *dock lokacji*. Okienka może mieć jeden z trzech typów nadrzędnych: lokacji dokowania, pasek dokowania lub okno ramowe minimalnej.  
  
 Istnieją dwa typy okienka: bez zmienny rozmiar i o zmiennym rozmiarze. Zmienny rozmiar okienka, takie jak paski stanu i paski narzędzi, można zmieniać za pomocą rozdzielaczy lub suwaki. Zmienny rozmiar okienka można tworzyć kontenery (jedno okienko może być zadokowany do innego okienka tworzenia podziału między nimi). Jednak o zmiennym rozmiarze okienka nie można dołączyć (zadokowane) dokowania pasków.  
  
 Jeśli aplikacja używa bez zmienny rozmiar okienka, pobierz je z [CPane klasy](../mfc/reference/cpane-class.md).  Jeśli aplikacja korzysta z okienka o zmiennych rozmiarach, pochodzi z [CDockablePane — klasa](../mfc/reference/cdockablepane-class.md)  
  
## <a name="dock-site"></a>Dock lokacji  
 Dock lokacji (lub głównego okna ramowego) jest właścicielem wszystkich okienka i okna ramowe mini w aplikacji. Lokacja dock zawiera [CDockingManager](../mfc/reference/cdockingmanager-class.md) elementu członkowskiego. Ten element członkowski przechowuje listę wszystkich okienek, które należą do witryny dokowania. Lista jest uporządkowana tak, aby okienka utworzony w zewnętrznej krawędzi lokacji dokowania znajdują się na początku listy. Gdy w ramach ponownie rysuje lokacji dokowania, pętli tej listy i dostosowuje układ poszczególnych okienkach uwzględnienie bieżący prostokąt ograniczający lokacji dokowania. Możesz wywołać `AdjustDockingLayout` lub `RecalcLayout` po należy dostosować dokowania układ i ramach przekierowuje to wywołanie Menedżera dokowania.  
  
## <a name="dock-bars"></a>Paski doku.  
 Położenie każdego głównego okna ramowego *dokowania pasków* wraz z jego krawędzi. Pasek dokowania to okienko należącą do [CDockSite klasy](../mfc/reference/cdocksite-class.md). Dokowania pasków może akceptować obiektów pochodzących od [CPane](../mfc/reference/cpane-class.md), takich jak pasków narzędzi. Aby utworzyć dokowania pasków po zainicjowaniu głównego okna ramowego, należy wywołać `EnableDocking`. Aby włączyć automatyczne ukrywanie paski, należy wywołać `EnableAutoHideBars`. `EnableAutoHideBars` Tworzy [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md) obiekty i umieszcza je obok każdego dokowania paska.  
  
 Każdy pasek dock jest podzielona na wiersze dokowania. Dock wierszy są reprezentowane przez [CDockingPanesRow klasy](../mfc/reference/cdockingpanesrow-class.md). Każdy wiersz dock zawiera listę pasków narzędzi. Jeśli użytkownik stacje dokujące paska narzędzi lub paska narzędzi są przenoszone z jednego wiersza do drugiej w ramach tego samego dokowania paska, ramach tworzy nowy wiersz i odpowiednio zmienia rozmiar paska dokowania lub Ustawia położenie paska narzędzi w istniejącym wierszu.  
  
## <a name="mini-frame-windows"></a>Okna ramowe minimalnej  
 Okienko przestawne znajduje się w oknie ramowym minimalnej. Okna ramowe mini są reprezentowane przez dwie klasy: [klasy CMDITabInfo](../mfc/reference/cmditabinfo-class.md) (która może zawierać tylko jedno okienko) i [klasy CMultiPaneFrameWnd](../mfc/reference/cmultipaneframewnd-class.md) (mogącą zawierać kilku okienek). Aby float okienko w kodzie, należy wywołać [CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane). Po pojawia się okienko platformę automatycznie tworzy okno ramowe minimalnej i ramki mini okno zostanie okienko przestawne nadrzędnej. Jeśli stacje dokujące okienko przestawne, platformę resetuje jego elementu nadrzędnego, a okienko przestawne staje się dokowania pasek (pasków narzędzi) lub lokacji dokowania (dla o zmiennym rozmiarze okienka).  
  
## <a name="pane-dividers"></a>Okienko separatorów  
 Separator okienka (nazywana również suwaki lub rozdzielaczy) są reprezentowane przez [CPaneDivider klasy](../mfc/reference/cpanedivider-class.md). Gdy użytkownik stacje dokujące okienko, platformę tworzy separatorów okienku, niezależnie od tego, czy okienko jest zadokowany w lokacji dokowania lub w innym okienka. Do witryny dokowania stacje dokujące okienko, dzielnik jest nazywany *domyślne dzielnik*. Domyślne dzielnik jest odpowiedzialny za układ wszystkie dokowania okienka w witrynie dokowania. Menedżer dokowania przechowuje listę domyślnego okienka separatorów i listy okienka. Menedżerowie Dock jest odpowiedzialny za układ dokowania okienka.  
  
## <a name="containers"></a>Kontenery  
 Wszystkie o zmiennym rozmiarze okienka, gdy jest zadokowany do siebie, są obsługiwane w kontenerach. Kontenery są reprezentowane przez [CPaneContainer klasy](../mfc/reference/cpanecontainer-class.md). Każdy kontener ma wskaźniki do jej w lewym okienku, prawym okienku po lewej stronie kontenera podrzędnego, prawy kontenera podrzędnego i rozdzielacza między częściami lewy i prawy. (*Lewej* i *prawo* nie odwołują się do strony fizycznej, ale raczej ustalić gałęzie struktury drzewa.) W ten sposób możemy drzewa okienka i rozdzielaczy kompilacji i w związku z tym osiągnięcia złożonych układów okienek, które można zmienić rozmiar razem. `CPaneContainer` Klasa obsługuje drzewa kontenery; zachowuje również dwie listy okienka oraz suwaki, które znajdują się w tym drzewie. Okienko kontenera menedżerów zwykle są osadzone w suwaki domyślne i okna ramowe minimalnej, zawierających dodatkowe okienka.  
  
## <a name="auto-hide-control-bars"></a>Automatyczne ukrywanie paski sterowania  
 Domyślnie każdy `CDockablePane` obsługuje funkcję autoukrywania. Gdy użytkownik kliknie przycisk numeru pin na podpis `CDockablePane`, platformę zmienia okienku na tryb autoukrywania. Aby obsłużyć kliknięcie, tworzy platformę [klasy CMFCAutoHideBar](../mfc/reference/cmfcautohidebar-class.md) i [klasy CMFCAutoHideButton](../mfc/reference/cmfcautohidebutton-class.md) skojarzone z `CMFCAutoHideBar` obiektu. Platformę umieszcza nowy `CMFCAutoHideBar` na [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md). Platformę również dołącza `CMFCAutoHideButton` na pasku narzędzi. [Klasy CDockingManager](../mfc/reference/cdockingmanager-class.md) przechowuje `CDockablePane`.  
  
## <a name="tabbed-control-bars-and-outlook-bars"></a>Paski sterowania z kartami i paski programu Outlook  
 [Klasy CMFCBaseTabCtrl](../mfc/reference/cmfcbasetabctrl-class.md) implementuje podstawowe funkcje z kartami okno z kartami odłączane. Aby użyć `CMFCBaseTabCtrl` obiektów, zainicjować [klasy CBaseTabbedPane](../mfc/reference/cbasetabbedpane-class.md) w aplikacji. `CBaseTabbedPane` jest pochodną `CDockablePane` i obsługuje wskaźnik do `CMFCBaseTabCtrl` obiektu. `CBaseTabbedPane` Umożliwia użytkownikom dock, a następnie zmień rozmiar paski sterowania z kartami. Użyj [CDockablePane::AttachToTabWnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd) można dynamicznie utworzyć paski sterowania, które zadokowane i kartach.  
  
 Formantu paska Outlook również jest oparta na paski z kartami. [Klasy CMFCOutlookBar](../mfc/reference/cmfcoutlookbar-class.md) jest pochodną `CBaseTabbedPane`. Aby uzyskać więcej informacji o sposobie używania paska Outlook, zobacz [CMFCOutlookBar klasy](../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)

