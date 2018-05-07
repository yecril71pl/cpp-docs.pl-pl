---
title: 'Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 1) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2d55768f423feef3b5093ec0af6365aecfaafee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 1)
W tym przewodniku przedstawiono sposób modyfikowania istniejącej aplikacji MFC korzystanie ze Wstążki. Program Visual Studio obsługuje zarówno wstążki pakietu Office 2007 i Windows 7 scen wstążki. Aby uzyskać więcej informacji na temat interfejsu użytkownika wstążki, zobacz [wstążek](http://go.microsoft.com/fwlink/p/?linkid=129233) w witrynie MSDN.  
  
 W tym przewodniku modyfikuje klasycznego próbka Bazgroły MFC 1.0, która pozwala na rysunkach za pomocą myszy. Ta część przewodnika pokazano, jak zmodyfikować przykładowy bazgrołów Wyświetla pasek wstążki. [Część 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) dodaje więcej przycisków na pasku wstążki.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 [Przykłady Visual C++](../visual-cpp-samples.md)  
  
 [Przykłady Visual C++](../visual-cpp-samples.md)  
  
##  <a name="top"></a> Sekcje  
 Ta część przewodnika zawiera następujące sekcje:  
  
- [Zastąpienie klas podstawowych](#replaceclass)  
  
- [Dodawanie bitmap do projektu](#addbitmap)  
  
- [Dodawanie zasobu wstążki do projektu](#addribbon)  
  
- [Utworzenie wystąpienia pasek wstążki](#createinstance)  
  
- [Dodawanie kategorii wstążki](#addcategory)  
  
- [Ustawienie wyglądu aplikacji](#setlook)  
  
##  <a name="replaceclass"></a> Zastąpienie klas podstawowych  
 Aby przekonwertować aplikacji, która obsługuje menu do aplikacji, która obsługuje wstążki, musi pochodzić od zaktualizowane klasy podstawowej aplikacji, okno ramowe i klasy narzędzi. (Zalecamy czy możesz nie modyfikować oryginalnego przykładu bazgrołów; zamiast tego, wyczyść projekt bazgrołów, skopiuj go do innego katalogu, a następnie zmodyfikuj kopii.)  
  
#### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Zastąpienie klas podstawowych w aplikacji bazgrołów  
  
1.  W scribble.cpp, upewnij się, że `CScribbleApp::InitInstance` zawiera wywołanie [afxoleinit —](../mfc/reference/ole-initialization.md#afxoleinit).  
  
2.  Dodaj następujący kod do pliku stdafx.h.  
  
 ```  
    #include <afxcontrolbars.h>  
 ```  
  
3.  W scribble.h, należy zmodyfikować definicję `CScribbleApp` klasy, dzięki czemu jest pochodną [CWinAppEx klasy](../mfc/reference/cwinappex-class.md).  
  
 ```  
    class CScribbleApp: public CWinAppEx  
 ```  
  
4.  Bazgrołów 1.0 zostały zapisane, gdy aplikacje systemu Windows używane plik inicjujący (*.ini) w celu zapisywania danych preferencji użytkownika. Zamiast pliku inicjującego zmodyfikować bazgrołów do przechowywania preferencji użytkownika w rejestrze. Aby ustawić klucz rejestru i podstawowej, wpisz następujący kod w `CScribbleApp::InitInstance` po `LoadStdProfileSettings()` instrukcji.  
  
 ```  
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));

 SetRegistryBase(_T("Settings"));

 ```  
  
5.  Ramki głównej dla wielu aplikacji interfejsu (MDI) dokumentu nie jest pochodną `CMDIFrameWnd` klasy. Zamiast tego jest pochodną [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) klasy.  
  
     W plikach mainfrm.h i mainfrm.cpp Zamień wszystkie odwołania do `CMDIFrameWnd` z `CMDIFrameWndEx`.  
  
6.  W plikach childfrm.h i childfrm.cpp, Zastąp `CMDIChildWnd` z `CMDIChildWndEx`.  
  
     W childfrm. Plik h, Zastąp `CSplitterWnd` z `CSplitterWndEx`.  
  
7.  Zmodyfikuj paski narzędzi i paski stanu do używania nowych klas MFC.  
  
     W pliku mainfrm.h:  
  
    1.  Zastąp `CToolBar` z `CMFCToolBar`.  
  
    2.  Zastąp `CStatusBar` z `CMFCStatusBar`.  
  
8.  W pliku mainfrm.cpp:  
  
    1.  Zastąp `m_wndToolBar.SetBarStyle` z `m_wndToolBar.SetPaneStyle`  
  
    2.  Zastąp `m_wndToolBar.GetBarStyle` z `m_wndToolBar.GetPaneStyle`  
  
    3.  Zastąp `DockControlBar(&m_wndToolBar)` z `DockPane(&m_wndToolBar)`  
  
9. W pliku ipframe.cpp komentarz następujące trzy wiersze kodu.  
  
 ```  
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);

 pWndFrame->EnableDocking(CBRS_ALIGN_ANY);

    pWndFrame->DockPane(&m_wndToolBar);

 ```  
  
10. Jeśli zamierzasz statycznie Połącz swoją aplikację, Dodaj następujący kod na początku pliku zasobów (.rc) projektu.  
  
 ```  
    #include "afxribbon.rc"  
 ```  
  
     Plik afxribbon.rc zawiera zasoby, które są wymagane w czasie wykonywania. [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) zawiera ten plik automatycznie podczas tworzenia aplikacji.  
  
11. Zapisać zmiany, a następnie utworzyć i uruchomić aplikację.  
  
 [[Sekcje](#top)]  
  
##  <a name="addbitmap"></a> Dodawanie bitmap do projektu  
 Następnie cztery kroki tego przewodnika wymaga zasobów mapy bitowej. Możesz uzyskać odpowiednie map bitowych na różne sposoby:  
  
-   Użyj [edytory zasobów](../windows/resource-editors.md) do magazynu własne map bitowych. Lub użyj edytory zasobów do włączenia mapy bitowe z obrazów PNG przenośne sieci, które są dołączone [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]. Te obrazy są w `VS2008ImageLibrary` katalogu.  
  
     Interfejs użytkownika wstążki wymaga jednak, że niektóre mapy bitowe obsługuje obrazy przezroczyste. Bitmapy przezroczyste Użyj 32-bitowych pikseli, gdzie 24 bity Określ składniki czerwony, zielonemu i niebieskiemu koloru i zdefiniuj 8 bitów *kanału alfa* , który określa Przezroczystość koloru. Bieżący edytory zasobów można wyświetlać, ale nie modyfikować map bitowych pikseli 32-bitowych. W związku z tym użyj edytora zewnętrznego zamiast edytory zasobów do manipulowania bitmapy przezroczyste.  
  
-   Skopiuj plik odpowiedni zasób z innej aplikacji do projektu, a następnie zaimportuj map bitowych z tego pliku.  
  
 W tym przewodniku kopiuje pliki zasobów z aplikacji w katalogu przykładów.  
  
#### <a name="to-add-bitmaps-to-the-project"></a>Dodawanie bitmap do projektu  
  
1.  Skopiuj następujące pliki .bmp z katalogu zasobów za pomocą Eksploratora plików (`res`) próbki RibbonGadgets:  
  
    1.  Skopiuj main.bmp bazgrołów projektu.  
  
    2.  Skopiuj filesmall.bmp i filelarge.bmp do projektu bazgrołów.  
  
    3.  Nowe kopie plików filelarge.bmp i filesmall.bmp, ale Zapisz kopie w przykładowym RibbonGadgets. Zmień nazwę kopii homesmall.bmp i homelarge.bmp, a następnie przenieść kopie projektu bazgrołów.  
  
    4.  Utwórz kopię pliku toolbar.bmp, ale zapisać kopię w przykładowym RibbonGadgets. Zmień nazwę panelicons.bmp kopiowania, a następnie przenieść kopię bazgrołów projektu.  
  
2.  Importowanie pliku mapy bitowej dla aplikacji MFC. W **widok zasobów**, kliknij dwukrotnie **scribble.rc** węzła, kliknij dwukrotnie **mapy bitowej** węzeł, a następnie kliknij przycisk **Dodaj zasób**. W oknie dialogowym kliknij polecenie **importu**. Przejdź do `res` katalogu, wybierz plik main.bmp, a następnie kliknij przycisk **Otwórz**.  
  
     Mapa bitowa main.bmp zawiera obraz 26 x 26. Zmień identyfikator mapy bitowej na IDB_RIBBON_MAIN.  
  
3.  Importuj bitmap do menu Plik, który jest dołączony do przycisku aplikacji.  
  
    1.  Importowanie pliku filesmall.bmp, który zawiera dziesięć 16 x 16 (16 x 160) obrazów. Ponieważ potrzebne tylko osiem 16 x 16 obrazów (16 x 128), należy użyć **widok zasobów** zmiany szerokości aktualnego ze 160 128. Zmień identyfikator mapy bitowej na IDB_RIBBON_FILESMALL.  
  
    2.  Importuj filelarge.bmp, który zawiera osiem 32 x 32 (32 x 256) obrazów. Zmień identyfikator mapy bitowej na IDB_RIBBON_FILELARGE.  
  
4.  Importowanie kategorii Wstążkę i panele map bitowych. Każdej karcie na pasku wstążki jest kategorią i składa się z etykiety tekstowej oraz opcjonalny obraz.  
  
    1.  Importuj bitową homesmall.bmp, która zawiera osiem 16 x 16 obrazy mapy bitowe przycisków mała. Zmień identyfikator mapy bitowej na IDB_RIBBON_HOMESMALL.  
  
    2.  Importuj bitową homelarge.bmp, która zawiera osiem 32 x 32 obrazy mapy bitowe przycisków duże. Zmień identyfikator mapy bitowej na IDB_RIBBON_HOMELARGE.  
  
5.  Importuj map bitowych panele po zmianie rozmiaru wstążki. Te map bitowych lub ikony panelu są używane po operacji zmiany rozmiaru, jeśli wstążki jest za mały, aby wyświetlić całą panel.  
  
    1.  Importuj mapy bitowej panelicons.bmp, który zawiera osiem 16 x 16 obrazów. W **właściwości** okna **edytora mapy bitowej**, Dostosuj szerokość mapy bitowej do 64 (16 x 64). Zmień identyfikator mapy bitowej na IDB_PANEL_ICONS.  
  
 [[Sekcje](#top)]  
  
##  <a name="addribbon"></a> Dodawanie zasobu wstążki do projektu  
 Podczas konwertowania aplikacji korzystającej z menu do aplikacji, która używa wstążki, nie trzeba usunąć lub wyłączyć istniejące menu. Zamiast tego utwórz zasób wstążki, dodawanie przycisków Wstążki i następnie skojarzyć nowe przyciski z istniejącymi elementami menu. Mimo że menu nie są już widoczne, wiadomości w pasku wstążki są przesyłane za pośrednictwem menu. Ponadto menu skrótów kontynuować pracę.  
  
 Wstążka składa się z przycisku aplikacji, który jest duży przycisk w lewej górnej części wstążki, i co najmniej jednej karty kategorii. Każda karta kategoria zawiera co najmniej jeden panele, które działają jak kontenery przycisków Wstążki i kontrolek. Poniższa procedura przedstawia sposób tworzenia zasobu wstążki, a następnie dostosować przycisku aplikacji.  
  
#### <a name="to-add-a-ribbon-resource-to-the-project"></a>Aby dodać zasób wstążki do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **dodawania zasobów**.  
  
2.  W **dodawania zasobów** okno dialogowe, wybierz opcję **wstążki** , a następnie kliknij przycisk **nowy**.  
  
     Visual Studio tworzy zasób Wstążki i otwarcie go w widoku Projekt. Identyfikator zasobu wstążki jest IDR_RIBBON1, która jest wyświetlana w **widok zasobów**. Wstążka zawiera jedną kategorię i jednego panelu.  
  
3.  Przycisk aplikacji można dostosować, modyfikując jego właściwości. Identyfikatory komunikatów, które są używane w ten kod jest już zdefiniowany w menu Bazgroły 1.0.  
  
4.  W widoku Projekt kliknij przycisk aplikacji, aby wyświetlić jego właściwości. Zmień wartości właściwości w następujący sposób: **obrazu** do `IDB_RIBBON_MAIN`, **monitu** do `File`, **klucze** do `f`, **duże obrazy** do `IDB_RIBBON_FILELARGE`, i **małe obrazy** do `IDB_RIBBON_FILESMALL`.  
  
5.  Poniższe modyfikacje tworzenie menu wyświetlanym po kliknięciu przycisku aplikacji. Kliknij przycisk wielokropka (**...** ) obok pozycji **elementy główne** otworzyć **Edytor elementów**.  
  
    1.  Kliknij przycisk **Dodaj** w celu dodania przycisku. Zmień **podpis** do `&New`, **identyfikator** do `ID_FILE_NEW`, **obrazu** do `0`, **duży obraz** do `0`.  
  
    2.  Kliknij przycisk **Dodaj** w celu dodania drugiego przycisku. Zmień **podpis** do `&Save`, **identyfikator** do `ID_FILE_SAVE`, **obrazu** do `2`, i **duży obraz** do `2`.  
  
    3.  Kliknij przycisk **Dodaj** na trzeci przycisk Dodaj. Zmień **podpis** do `Save &As`, **identyfikator** do `ID_FILE_SAVE_AS`, **obrazu** do `3`, i **duży obraz** do `3`.  
  
    4.  Kliknij przycisk **Dodaj** do czwarty przycisk Dodaj. Zmień **podpis** do `&Print`, **identyfikator** do `ID_FILE_PRINT`, **obrazu** do `4`, i **duży obraz** do `4`.  
  
    5.  Zmień **elementu** typ **separatora** , a następnie kliknij przycisk **Dodaj**.  
  
    6.  Zmień **elementu** typ **przycisk**. Kliknij przycisk **Dodaj** do piąty przycisk Dodaj. Zmień **podpis** do `&Close`, **identyfikator** do `ID_FILE_CLOSE`, **obrazu** do `5`, i **duży obraz** do `5`.  
  
6.  Poniższe modyfikacje utworzyć podmenu po kliknięciu przycisku Drukuj utworzony w poprzednim kroku.  
  
    1.  Kliknij przycisk **drukowania** przycisku, zmień **elementu** typ **etykiety**, a następnie kliknij przycisk **Wstaw**. Zmień **podpis** do `Preview and print the document`.  
  
    2.  Kliknij przycisk **drukowania** przycisku, zmień **elementu** typ **przycisk**i kliknij przycisk **Wstaw**. Zmień **podpis** do `&Print`, **identyfikator** do `ID_FILE_PRINT`, **obrazu** do `4`, i **duży obraz** do `4`.  
  
    3.  Kliknij przycisk **drukowania** przycisk, a następnie kliknij przycisk **Wstaw** w celu dodania przycisku. Zmień **podpis** do `&Quick Print`, **identyfikator** do `ID_FILE_PRINT_DIRECT`, **obrazu** do `7`, i **duży obraz** do `7`.  
  
    4.  Kliknij przycisk **drukowania** przycisk, a następnie kliknij przycisk **Wstaw** można dodać inny przycisk. Zmień **podpis** do `Print Pre&view`, **identyfikator** do `ID_FILE_PRINT_PREVIEW`, **obrazu** do `6`, i **duży obraz** do `6`.  
  
    5.  Teraz zmodyfikowano **elementy główne**. Kliknij przycisk **Zamknij** aby zakończyć **Edytor elementów**.  
  
7.  Po dokonaniu zmiany tworzy przycisk Zakończ, wyświetlonym u dołu menu przycisku aplikacji.  
  
    1.  W **właściwości** okna, kliknij przycisk wielokropka (**...** ) obok pozycji **przycisk** otworzyć **Edytor elementów**.  
  
    2.  Kliknij przycisk **Dodaj** w celu dodania przycisku. Zmień **podpis** do `E&xit`, **identyfikator** do `ID_APP_EXIT`, **obrazu** do `8`.  
  
 [[Sekcje](#top)]  
  
##  <a name="createinstance"></a> Utworzenie wystąpienia pasek wstążki  
 Poniższe kroki pokazują, jak utworzyć wystąpienia pasek wstążki podczas uruchamiania aplikacji. Aby dodać pasek wstążki do aplikacji, należy zadeklarować na pasku wstążki w pliku mainfrm.h. Następnie w pliku mainfrm.cpp napisz kod umożliwiający ładowanie zasobu wstążki.  
  
#### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Aby utworzyć wystąpienie pasek wstążki  
  
1.  W pliku mainfrm.h, należy dodać element członkowski danych do sekcji chronionych `CMainFrame`, definicji klasy dla ramki głównej. Ten element członkowski reprezentuje pasek wstążki.  
  
 "" * / / Wstążki paska aplikacji  
    CMFCRibbonBar m_wndRibbonBar;  
 ```  
  
2.  In the mainfrm.cpp file, add the following code before the final `return` statement at the end of the `CMainFrame::OnCreate` function. This creates an instance of the ribbon bar.  
  
 ``` *// Create the ribbon bar  
    if (!m_wndRibbonBar.Create(this))  
 {  
    return -1;   //Failed to create ribbon bar  
 }  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

 ```  
  
 [[Sekcje](#top)]  
  
##  <a name="addcategory"></a> Dostosowywanie zasób wstążki  
 Teraz, po utworzeniu przycisku aplikacji, można dodać elementów do wstążki.  
  
> [!NOTE]
>  W tym przewodniku zastosowano ikonę Panelu takie same dla wszystkich paneli. Jednak można użyć innych indeksy listy obrazów do wyświetlania innych ikon.  
  
#### <a name="to-add-a-home-category-and-edit-panel"></a>Aby dodać głównej kategorii i edytować panelu  
  
1.  Program bazgrołów wymaga tylko jedną kategorię. W widoku Projekt, kliknij przycisk **kategorii** Aby wyświetlić jego właściwości. Zmień wartości właściwości w następujący sposób: **podpis** do `&Home`, **duże obrazy** do `IDB_RIBBON_HOMELARGE`, **małe obrazy** do `IDB_RIBBON_HOMESMALL`.  
  
2.  Każda kategoria wstążki jest podzielony na nazwanym paneli. Każdy panel zawiera zestaw kontrolek, które wykonują operacje pokrewne. Ta kategoria zawiera jednego panelu. Kliknij przycisk **panelu**, a następnie zmień **podpis** do `Edit` i **indeks obrazu** do `0`.  
  
3.  Aby **Edytuj** panelu, Dodawanie przycisku, który jest odpowiedzialny za wyczyszczenie zawartości dokumentu. Identyfikator komunikatu dla tego przycisku został już zdefiniowany w zasobie menu IDR_SCRIBBTYPE. Określ `Clear All` jako tekst przycisku i indeks mapy bitowej programu decorates przycisku. Otwórz **przybornika**, a następnie przeciągnij **przycisk** do **Edytuj** panelu. Kliknij przycisk, a następnie zmień **podpis** do `Clear All`, **identyfikator** do `ID_EDIT_CLEAR_ALL`, **indeks obrazu** do `0`, **indeks dużego obrazu**  do `0`.  
  
4.  Zapisać zmiany, a następnie kompilacji i uruchomić aplikację. Aplikacji bazgrołów powinien być wyświetlany, a powinien mieć pasek wstążki w górnej części okna zamiast paska menu. Pasek wstążki powinny mieć jedną kategorię **Home**, i **Home** powinien mieć jeden panel **Edytuj**. Przyciski wstążki, który został dodany powinna być skojarzona z istniejących programów obsługi zdarzeń i **Otwórz**, **Zamknij**, **zapisać**, **drukowania**, i **Wyczyść wszystko** przyciski powinny działać zgodnie z oczekiwaniami.  
  
 [[Sekcje](#top)]  
  
##  <a name="setlook"></a> Ustawienie wyglądu aplikacji  
 A *Menedżera visual* jest globalny obiekt, który kontroluje wszystkie rysunku dla aplikacji. Ponieważ oryginalne aplikacji bazgrołów używa styl interfejsu użytkownika pakietu Office 2000, aplikacja może wyglądać stosowane. Możesz resetować aplikacji tak, aby podobny do aplikacji pakietu Office 2007 za pomocą Menedżera visual Office 2007.  
  
#### <a name="to-set-the-look-of-the-application"></a>Aby ustawić wygląd aplikacji  
  
1.  W `CMainFrame::OnCreate` , wpisz następujący kod, aby zmienić domyślnego menedżera visual i styl.  
  
 "" * / / Ustaw domyślnego menedżera pakietu Office 2007   
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));

 CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);

 ```  
  
2.  Save the changes, and then build and run the application. The application UI should resemble the Office 2007 UI.  
  
 [[Sections](#top)]  
  
## Next Steps  
 You have modified the classic Scribble 1.0 MFC sample to use the Ribbon Designer. Now go to [Part 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)

