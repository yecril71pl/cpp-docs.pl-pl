---
title: 'Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 1)'
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 9fc2903180a055c18c6f3779b1da55ee347d2535
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230431"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 1)

W tym instruktażu przedstawiono sposób modyfikowania istniejącej aplikacji MFC do korzystania z interfejsu użytkownika wstążki. Program Visual Studio obsługuje zarówno wstążkę pakietu Office 2007, jak i Wstążkę Scenic systemu Windows 7. Aby uzyskać więcej informacji na temat interfejsu użytkownika wstążki, zobacz [wstążki](/windows/win32/uxguide/cmd-ribbons).

W tym instruktażu jest modyfikowany przykład klasycznego programu Bazgroły 1,0 MFC, który umożliwia tworzenie rysunków liniowych za pomocą myszy. W tej części przewodnika pokazano, jak zmodyfikować przykład Bazgroły, aby wyświetlał pasek wstążki. [Część 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) dodaje do paska wstążki więcej przycisków.

## <a name="prerequisites"></a>Wymagania wstępne

[Przykład programu Bazgroły dla MFC 1,0](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Aby uzyskać pomoc dotyczącą konwersji do programu Visual Studio 2017 lub nowszego, zobacz [Przewodnik dotyczący przenoszenia danych: Bazgroły MFC](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a>Poszczególne

Ta część przewodnika zawiera następujące sekcje:

- [Zamienianie klas bazowych](#replaceclass)

- [Dodawanie map bitowych do projektu](#addbitmap)

- [Dodawanie zasobu wstążki do projektu](#addribbon)

- [Tworzenie wystąpienia paska wstążki](#createinstance)

- [Dodawanie kategorii wstążki](#addcategory)

- [Ustawianie wyglądu aplikacji](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>Zamienianie klas bazowych

Aby skonwertować aplikację, która obsługuje menu w aplikacji, która obsługuje Wstążkę, należy uzyskać pochodną klasy aplikacji, ramki i narzędzi z zaktualizowanych klas bazowych. (Sugerujemy, aby nie modyfikować oryginalnego przykładu bazgrołów. Zamiast tego Wyczyść projekt Bazgroły, skopiuj go do innego katalogu, a następnie zmodyfikuj kopię.

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Aby zastąpić klasy bazowe w aplikacji Bazgroły

1. W oknie Bazgroły. cpp Sprawdź, czy `CScribbleApp::InitInstance` zawiera wywołanie [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Dodaj następujący kod do pliku *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i jego starszych):

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. W oknie Bazgroły. h zmodyfikuj definicję klasy, `CScribbleApp` tak aby była ona pochodną [klasy CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Bazgroły 1,0 zostały zapisane, gdy aplikacje systemu Windows używały pliku inicjującego (. ini) do zapisywania danych preferencji użytkownika. Zamiast pliku inicjującego należy zmodyfikować Bazgroły, aby zachować preferencje użytkownika w rejestrze. Aby ustawić klucz rejestru i bazę, wpisz poniższy kod w `CScribbleApp::InitInstance` `LoadStdProfileSettings()` instrukcji After.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Ramka główna dla aplikacji interfejsu wielu dokumentów (MDI) nie jest już wyprowadzana z `CMDIFrameWnd` klasy. Zamiast tego jest on pochodny klasy [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) .

    W plikach MainFrm. h i MainFrm. cpp Zastąp wszystkie odwołania do `CMDIFrameWnd` `CMDIFrameWndEx` .

1. W plikach childfrm. h i childfrm. cpp Zastąp ciąg `CMDIChildWnd` `CMDIChildWndEx` .

    W childfrm. h plik, Zamień `CSplitterWnd` na `CSplitterWndEx` .

1. Modyfikuj paski narzędzi i paski stanu, aby użyć nowych klas MFC.

    W pliku mainfrm. h:

    1. Zastąp element `CToolBar` pytaniem `CMFCToolBar`.

    1. Zastąp element `CStatusBar` pytaniem `CMFCStatusBar`.

1. W pliku mainfrm. cpp:

    1. Zamień `m_wndToolBar.SetBarStyle` na`m_wndToolBar.SetPaneStyle`

    1. Zamień `m_wndToolBar.GetBarStyle` na`m_wndToolBar.GetPaneStyle`

    1. Zamień `DockControlBar(&m_wndToolBar)` na`DockPane(&m_wndToolBar)`

1. W pliku ipframe. cpp Skomentuj następujące trzy wiersze kodu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Zapisz zmiany, a następnie Skompiluj i uruchom aplikację.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>Dodawanie map bitowych do projektu

Kolejne cztery kroki tego instruktażu wymagają zasobów map bitowych. Odpowiednie mapy bitowe można uzyskać na różne sposoby:

- Użyj [edytorów zasobów](../windows/resource-editors.md) , aby wyrównać własne mapy bitowe. Lub użyj edytorów zasobów, aby utworzyć mapy bitowe z obrazów Portable Network Graphics (PNG), które są dołączone do programu Visual Studio i można pobrać z [biblioteki obrazów programu Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Jednak interfejs użytkownika **wstążki** wymaga, aby niektóre mapy bitowe obsługiwały przezroczyste obrazy. Przezroczyste mapy bitowe używają 32-bitowych pikseli, gdzie 24 bity określają składniki czerwonego, zielonego i niebieskiego koloru, a 8 bitów definiuje *kanał alfa* , który określa przezroczystość koloru. Bieżące edytory zasobów mogą wyświetlać, ale nie modyfikować Bitmap z 32-bitowymi pikselami. W związku z tym Użyj zewnętrznego edytora obrazów zamiast edytorów zasobów, aby manipulować przezroczystymi mapami bitowych.

- Skopiuj odpowiedni plik zasobów z innej aplikacji do projektu, a następnie zaimportuj mapy bitowe z tego pliku.

Ten Instruktaż kopiuje pliki zasobów z przykładu utworzonego w [przewodniku: Tworzenie aplikacji wstążki za pomocą MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Aby dodać mapy bitowe do projektu

1. Za pomocą Eksploratora plików Skopiuj następujące pliki BMP z katalogu zasobów ( `res` ) przykładowej wstążki do katalogu zasobów ( `res` ) projektu bazgrołowego:

   1. Skopiuj main.bmp do projektu Bazgrołowego.

   1. Skopiuj filesmall.bmp i filelarge.bmp do projektu Bazgroły.

   1. Utwórz nowe kopie filelarge.bmp i filesmall.bmp plików, ale Zapisz kopie na przykładzie wstążki. Zmień nazwę kopii homesmall.bmp i homelarge.bmp a następnie przenieś kopie do projektu bazgrołów.

   1. Utwórz kopię pliku toolbar.bmp, ale Zapisz kopię na Wstążce przykład. Zmień nazwę kopii panelicons.bmp a następnie Przenieś kopię do projektu Bazgroły.

1. Zaimportuj mapę bitową dla aplikacji MFC. W **Widok zasobów**kliknij dwukrotnie węzeł **Bazgroły. RC** , kliknij dwukrotnie węzeł **Mapa bitowa** , a następnie kliknij pozycję **Dodaj zasób**. W wyświetlonym oknie dialogowym kliknij przycisk **Importuj**. Przejdź do `res` katalogu, wybierz plik main.bmp, a następnie kliknij przycisk **Otwórz**.

   Mapa bitowa main.bmp zawiera obraz 26x26. Zmień identyfikator mapy bitowej na `IDB_RIBBON_MAIN` .

1. Zaimportuj mapy bitowe dla menu plik, które jest dołączone do przycisku **aplikacji** .

   1. Zaimportuj plik filesmall.bmp zawierający jedenaście obrazów 16x16 (16x176). Zmień identyfikator mapy bitowej na `IDB_RIBBON_FILESMALL` .

   > [!NOTE]
   > Ponieważ potrzebujemy tylko pierwszych ośmiu obrazów 16x16 (16x128), możesz opcjonalnie przyciąć prawą szerokość tej mapy bitowej z 176 do 128.

   1. Zaimportuj filelarge.bmp, który zawiera dziewięć obrazów 32x32 (32x288). Zmień identyfikator mapy bitowej na `IDB_RIBBON_FILELARGE` .

1. Zaimportuj mapy bitowe dla kategorii i paneli wstążki. Każda karta na pasku wstążki jest kategorią i składa się z etykiety tekstowej i opcjonalnego obrazu.

   1. Zaimportuj mapę bitową homesmall.bmp, która zawiera jedenaście obrazów 16x16 dla małych map bitowych przycisków. Zmień identyfikator mapy bitowej na `IDB_RIBBON_HOMESMALL` .

   1. Zaimportuj mapę bitową homelarge.bmp, która zawiera dziewięć obrazów 32x32 dla map bitowych dużych przycisków. Zmień identyfikator mapy bitowej na `IDB_RIBBON_HOMELARGE` .

1. Importuj mapy bitowe dla paneli wstążki o zmienionym rozmiarze. Te mapy bitowe lub ikony panelu są używane po operacji zmiany rozmiaru, jeśli wstążka jest zbyt mała, aby wyświetlić cały panel.

   1. Zaimportuj mapę bitową panelicons.bmp, która zawiera osiem obrazów 16x16. W oknie **Właściwości** **edytora mapy bitowej**Dostosuj szerokość mapy bitowej do 64 (16x64). Zmień identyfikator mapy bitowej na `IDB_PANEL_ICONS` .

   > [!NOTE]
   > Ponieważ potrzebujemy tylko czterech pierwszych obrazów (16x64), możesz opcjonalnie przyciąć prawą szerokość tej mapy bitowej z 128 do 64.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>Dodawanie zasobu wstążki do projektu

Podczas konwertowania aplikacji, która używa menu do aplikacji, która używa wstążki, nie trzeba usuwać ani wyłączać istniejących menu. Po prostu utwórz zasób wstążki, Dodaj przyciski wstążki, a następnie skojarz nowe przyciski z istniejącymi elementami menu. Mimo że menu nie są już widoczne, komunikaty z paska wstążki są kierowane w menu i skróty do menu nadal działają.

Wstążka składa się z przycisku **aplikacji** , który jest dużym przyciskiem w lewej górnej części wstążki oraz co najmniej jedną kartę kategorii. Każda karta kategorii zawiera jeden lub więcej paneli, które działają jako kontenery dla przycisków wstążki i kontrolek. Poniższa procedura pokazuje, jak utworzyć zasób wstążki, a następnie dostosować przycisk **aplikacji** .

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Aby dodać zasób wstążki do projektu

1. Z projektem bazgrołów wybranym w **Eksplorator rozwiązań**w menu **projekt** kliknij polecenie **Dodaj zasób**.

1. W oknie dialogowym **Dodawanie zasobu** wybierz **Wstążkę** , a następnie kliknij przycisk **Nowy**.

   Program Visual Studio tworzy zasób wstążki i otwiera go w widoku projektu. Identyfikator zasobu wstążki to `IDR_RIBBON1` , który jest wyświetlany w **Widok zasobów**. Wstążka zawiera jedną kategorię i jeden panel.

1. Przycisk **aplikacji** można dostosować, modyfikując jego właściwości. Identyfikatory komunikatów, które są używane w tym kodzie, są już zdefiniowane w menu dla bazgrołów 1,0.

1. W widoku Projekt kliknij przycisk **aplikacja** , aby wyświetlić jego właściwości. Zmień wartości właściwości w następujący sposób: **obraz** z `IDB_RIBBON_MAIN` , **Monituj** do `File` , **klawisze** do `f` , **duże obrazy** do `IDB_RIBBON_FILELARGE` i **małe obrazy** `IDB_RIBBON_FILESMALL` .

1. Poniższe modyfikacje tworzą menu, które pojawiają się, gdy użytkownik kliknie przycisk **aplikacji** . Kliknij przycisk wielokropka (**...**) obok **pozycji główne elementy** , aby otworzyć **Edytor elementów**.

   1. Po wybraniu **przycisku** typ **elementu** kliknij przycisk **Dodaj** , aby dodać przycisk. Zmień **napis** na `&New` , **Identyfikator** na `ID_FILE_NEW` , **obraz** do `0` , **duży obraz** `0` .

   1. Kliknij przycisk **Dodaj** , aby dodać przycisk. Zmień **napis** na `&Save` , **Identyfikator** na `ID_FILE_SAVE` , **obraz** do `2` i **obraz duże** do `2` .

   1. Kliknij przycisk **Dodaj** , aby dodać przycisk. Zmień **napis** na `Save &As` , **Identyfikator** na `ID_FILE_SAVE_AS` , **obraz** do `3` i **obraz duże** do `3` .

   1. Kliknij przycisk **Dodaj** , aby dodać przycisk. Zmień **napis** na `&Print` , **Identyfikator** na `ID_FILE_PRINT` , **obraz** do `4` i **obraz duże** do `4` .

   1. Zmień typ **elementu** na **separator** , a następnie kliknij przycisk **Dodaj**.

   1. Zmień typ **elementu** na **przycisk**. Kliknij przycisk **Dodaj** , aby dodać piąty przycisk. Zmień **napis** na `&Close` , **Identyfikator** na `ID_FILE_CLOSE` , **obraz** do `5` i **obraz duże** do `5` .

1. Poniższe modyfikacje tworzą podmenu w ramach przycisku **Drukuj** utworzonego w poprzednim kroku.

   1. Kliknij przycisk **Drukuj** , Zmień typ **elementu** na **etykieta**, a następnie kliknij przycisk **Wstaw**. Zmień **napis** na `Preview and print the document` .

   1. Kliknij przycisk **Drukuj** , Zmień typ **elementu** na **przycisk**, a następnie kliknij przycisk **Wstaw**. Zmień **napis** na `&Print` , **Identyfikator** na `ID_FILE_PRINT` , **obraz** do `4` i **obraz duże** do `4` .

   1. Kliknij przycisk **Drukuj** , a następnie kliknij przycisk **Wstaw** , aby dodać przycisk. Zmień **napis** na `&Quick Print` , **Identyfikator** na `ID_FILE_PRINT_DIRECT` , **obraz** do `7` i **obraz duże** do `7` .

   1. Kliknij przycisk **Drukuj** , a następnie kliknij przycisk **Wstaw** , aby dodać inny przycisk. Zmień **napis** na `Print Pre&view` , **Identyfikator** na `ID_FILE_PRINT_PREVIEW` , **obraz** do `6` i **obraz duże** do `6` .

   1. **Elementy główne**zostały już zmodyfikowane. Kliknij przycisk **Zamknij** , aby wyjść z **edytora elementów**.

1. Poniższe modyfikacje tworzą przycisk zakończenia, który pojawia się w dolnej części menu przycisku **aplikacji** .

   1. Wybierz kartę **Widok zasobów** w **Eksplorator rozwiązań**.
   1. W oknie **Właściwości** kliknij przycisk wielokropka (**...**) obok **przycisku** , aby otworzyć **Edytor elementów**.

   1. Po wybraniu **przycisku** typ **elementu** kliknij przycisk **Dodaj** , aby dodać przycisk. Zmień **napis** na `E&xit` , **Identyfikator** na `ID_APP_EXIT` , **obraz** do `8` .

   1. Zmodyfikowano **przyciski**. Kliknij przycisk **Zamknij** , aby wyjść z **edytora elementów**.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>Tworzenie wystąpienia paska wstążki

Poniższe kroki pokazują, jak utworzyć wystąpienie paska wstążki podczas uruchamiania aplikacji. Aby dodać pasek wstążki do aplikacji, zadeklaruj pasek wstążki w pliku mainfrm. h. Następnie w pliku mainfrm. cpp Napisz kod w celu załadowania zasobu wstążki.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Aby utworzyć wystąpienie paska wstążki

1. W pliku mainfrm. h Dodaj element członkowski danych do chronionej sekcji `CMainFrame` , definicję klasy dla ramki głównej. Ten element członkowski jest przeznaczony dla paska wstążki.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. W pliku mainfrm. cpp Dodaj następujący kod przed **`return`** instrukcją końcową na końcu `CMainFrame::OnCreate` funkcji. Tworzy wystąpienie paska wstążki.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>Dostosowywanie zasobu wstążki

Po utworzeniu przycisku **aplikacji** możesz dodać elementy do wstążki.

> [!NOTE]
> W tym instruktażu zostanie użyta ta sama ikona panelu dla wszystkich paneli. Można jednak użyć innych indeksów listy obrazów, aby wyświetlić inne ikony.

### <a name="to-add-a-home-category-and-edit-panel"></a>Aby dodać kategorię główną i panel edycji

1. Program Bazgroły wymaga tylko jednej kategorii. W widoku Projekt w **przyborniku**kliknij dwukrotnie **kategorię Kategoria** , aby dodać ją i wyświetlić jej właściwości. Zmień wartości właściwości w następujący sposób: **Caption** do `&Home` , **duże obrazy** do `IDB_RIBBON_HOMELARGE` , do **małych obrazów** `IDB_RIBBON_HOMESMALL` .

1. Każda kategoria wstążki jest zorganizowana w nazwane panele. Każdy panel zawiera zestaw kontrolek, które ukończą powiązane operacje. Ta kategoria ma jeden panel. Kliknij **panel**, a następnie zmień **napis** na `Edit` .

1. Do panelu **Edycja** Dodaj przycisk odpowiedzialny za wyczyszczenie zawartości dokumentu. Identyfikator komunikatu dla tego przycisku został już zdefiniowany w `IDR_SCRIBBTYPE` menu zasób. Określ `Clear All` jako tekst przycisku i indeks mapy bitowej, która zdobi przycisk. Otwórz **Przybornik**, a następnie przeciągnij **przycisk** do panelu **Edycja** . Kliknij przycisk, a następnie zmień **podpis** na `Clear All` , **Identyfikator** do, `ID_EDIT_CLEAR_ALL` **indeks obrazu** , na który ma `0` być **indeks dużego obrazu** `0` .

1. Zapisz zmiany, a następnie Skompiluj i uruchom aplikację. Aplikacja bazgrołów powinna być wyświetlana, a w górnej części okna powinna znajdować się pasek wstążki, a nie pasek menu. Pasek wstążki powinien mieć jedną kategorię, **Home**i **Home** powinien mieć jeden panel, **Edytuj**. Dodane przyciski wstążki powinny być skojarzone z istniejącymi programami obsługi zdarzeń, a przyciski **Otwórz**, **Zamknij**, **Zapisz**, **Drukuj**i **Wyczyść wszystkie** powinny działać zgodnie z oczekiwaniami.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>Ustawianie wyglądu aplikacji

*Program Visual Manager* jest obiektem globalnym, który kontroluje cały rysunek dla aplikacji. Ponieważ oryginalna aplikacja bazgrołów używa stylu interfejsu użytkownika (UI) pakietu Office 2000, aplikacja może wyglądać w stary sposób. Możesz zresetować aplikację tak, aby korzystała z programu Microsoft Visual 2007e Manager, tak aby była podobna do aplikacji pakietu Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Aby ustawić wygląd aplikacji

1. W `CMainFrame::OnCreate` funkcji wpisz poniższy kod przed `return 0;` instrukcją zmiany domyślnego menedżera i stylu wizualnego.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Zapisz zmiany, a następnie Skompiluj i uruchom aplikację. Interfejs użytkownika aplikacji powinien wyglądać podobnie do interfejsu użytkownika pakietu Office 2007.

## <a name="next-steps"></a>Następne kroki

Zmodyfikowano przykład klasycznego bazgrołów 1,0 MFC, aby użyć **projektanta wstążki**. Teraz przejdź do [części 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Zobacz także

[Wskazówki](../mfc/walkthroughs-mfc.md)<br/>
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
