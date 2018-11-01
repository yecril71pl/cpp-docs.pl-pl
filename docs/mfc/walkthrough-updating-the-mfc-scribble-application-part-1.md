---
title: 'Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 1)'
ms.date: 09/20/2018
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 85ff0c17f8ec523fc5cb52101fb44cfc37dd9b50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481851"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 1)

W tym instruktażu pokazano, jak zmodyfikować istniejącą aplikację MFC przy użyciu interfejsu użytkownika wstążki. Program Visual Studio obsługuje zarówno wstążki pakietu Office 2007, jak i Windows 7 scen wstążki. Aby uzyskać więcej informacji na temat interfejsu użytkownika wstążki, zobacz [wstążek](/windows/desktop/uxguide/cmd-ribbons).

W tym przewodniku modyfikuje klasyczny przykład klasa Scribble MFC 1.0, który pozwala tworzyć rysunki wiersza za pomocą myszy. Tej części instruktażu pokazano, jak zmodyfikować próbki Bazgroły, tak, aby wyświetlał paska wstążki. [Część 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) dodaje więcej przycisków do paska wstążki.

## <a name="prerequisites"></a>Wymagania wstępne

[Próbki Bazgroły MFC 1.0](http://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Aby uzyskać pomoc dotyczącą konwersji do programu Visual Studio 2017, zobacz [przewodnik przenoszenia: klasa Scribble MFC](../porting/porting-guide-mfc-scribble.md).

##  <a name="top"></a> Sekcje

Ta część przewodnika zawiera następujące sekcje:

- [Zastąpienie klas bazowych](#replaceclass)

- [Dodawanie bitmap do projektu](#addbitmap)

- [Dodawanie zasobu wstążki do projektu](#addribbon)

- [Tworzenie wystąpienia paska wstążki](#createinstance)

- [Dodawanie kategorii wstążki](#addcategory)

- [Ustawienie wygląd aplikacji](#setlook)

##  <a name="replaceclass"></a> Zastąpienie klas bazowych

Aby przekonwertować aplikacji, która obsługuje menu do aplikacji, która obsługuje wstążki, musi pochodzić klasy narzędzi aplikacji, ramki okna i zaktualizowano klas podstawowych. (Zaleca się czy nie modyfikują oryginalnej próbki Bazgroły. Zamiast tego należy wyczyścić projektu Bazgroły, skopiuj go do innego katalogu, a następnie zmodyfikuj kopii.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Zastąpienie klas bazowych w aplikacji bazgrołów

1. W scribble.cpp, upewnij się, że `CScribbleApp::InitInstance` zawiera wywołanie [afxoleinit —](../mfc/reference/ole-initialization.md#afxoleinit).

1. Dodaj następujący kod do pliku stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. W scribble.h, należy zmodyfikować definicję dla `CScribbleApp` klasy tak, aby go jest tworzony na podstawie [klasa CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Bazgrołów 1.0 zostały zapisane, gdy aplikacje systemu Windows używane plik inicjujący (.ini) w celu zapisywania danych preferencji użytkownika. Zamiast pliku inicjującego zmodyfikować bazgrołów do przechowywania preferencji użytkownika w rejestrze. Aby ustawić klucz rejestru i podstawowa, wpisz następujący kod w `CScribbleApp::InitInstance` po `LoadStdProfileSettings()` instrukcji.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Ramy głównej dla wielu aplikacji interfejsu (MDI) dokumentu nie jest już jest tworzony na podstawie `CMDIFrameWnd` klasy. Zamiast tego jest pochodną [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) klasy.

    W plikach mainfrm.h i mainfrm.cpp, Zastąp wszystkie odwołania do `CMDIFrameWnd` z `CMDIFrameWndEx`.

1. W plikach childfrm.h i childfrm.cpp, Zastąp `CMDIChildWnd` z `CMDIChildWndEx`.

    W childfrm. Plik h, Zastąp `CSplitterWnd` z `CSplitterWndEx`.

1. Zmodyfikuj paski narzędzi i stanu używać nowych klas MFC.

    W pliku mainfrm.h:

    1. Zastąp `CToolBar` z `CMFCToolBar`.

    1. Zastąp `CStatusBar` z `CMFCStatusBar`.

1. W pliku mainfrm.cpp:

    1. Zastąp `m_wndToolBar.SetBarStyle` z `m_wndToolBar.SetPaneStyle`

    1. Zastąp `m_wndToolBar.GetBarStyle` z `m_wndToolBar.GetPaneStyle`

    1. Zastąp `DockControlBar(&m_wndToolBar)` z `DockPane(&m_wndToolBar)`

1. W pliku ipframe.cpp komentarz następujące trzy wiersze kodu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Zapisz zmiany, a następnie tworzenie i uruchamianie aplikacji.

##  <a name="addbitmap"></a> Dodawanie bitmap do projektu

Czterech kolejnych krokach w tym przewodniku wymaga zasobów mapy bitowej. Możesz uzyskać odpowiednie map bitowych na różne sposoby:

- Użyj [edytory zasobów](../windows/resource-editors.md) wymyślaniem własne map bitowych. Lub użyj edytory zasobów, aby złożyć mapy bitowej przy użyciu obrazów graphics (PNG) sieci przenośnych, które są dołączone do programu Visual Studio i można go pobrać ze [Biblioteka obrazów programu Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Jednak **wstążki** interfejsu użytkownika wymaga, że niektóre mapy bitowe obsługują obrazy przezroczyste. Bitmapy przezroczyste użyć 32-bitowych pikseli, gdzie 24 bity Określ składników czerwonego, zielonego i niebieskiego koloru i zdefiniuj 8 bitów *kanał alfa* , który określa Przezroczystość koloru. Bieżący edytory zasobów można wyświetlić, ale nie modyfikować bitmapy z 32-bitowych pikseli. W związku z tym użyj edytora zewnętrznego zamiast edytory zasobów do manipulowania mapy bitowe przezroczysty.

- Skopiuj plik odpowiedni zasób z innej aplikacji do projektu, a następnie zaimportuj map bitowych z tego pliku.

W tym przewodniku kopiuje pliki zasobów z przykładu, utworzone w [wskazówki: tworzenie Wstążki aplikacji przy użyciu MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Dodawanie bitmap do projektu

1. Skopiuj następujące pliki .bmp z katalogu zasobów za pomocą Eksploratora plików (`res`) przykładu wstążki do katalogu zasobów (`res`) bazgrołów projektu:

   1. Skopiuj main.bmp bazgrołów projektu.

   1. Skopiuj filesmall.bmp i filelarge.bmp do projektu bazgrołów.

   1. Utwórz nowe kopie plików filelarge.bmp i filesmall.bmp, ale zapisywać kopie w przykładzie wstążki. Zmień nazwę kopii homesmall.bmp i homelarge.bmp, a następnie przenieść kopie bazgrołów projektu.

   1. Utwórz kopię pliku toolbar.bmp, ale zapisać kopię w przykładzie wstążki. Zmień nazwę panelicons.bmp kopiowania, a następnie przenieś kopiowania do projektu bazgrołów.

1. Importuj mapy bitowej dla aplikacji MFC. W **widok zasobów**, kliknij dwukrotnie **scribble.rc** węzła, kliknij dwukrotnie **mapy bitowej** węzłem, a następnie kliknij przycisk **Dodaj zasób**. W oknie dialogowym kliknij **importu**. Przejdź do `res` katalogu, wybierz plik main.bmp, a następnie kliknij przycisk **Otwórz**.

   Mapa bitowa main.bmp zawiera obraz 26 x 26. Zmień identyfikator mapy bitowej do `IDB_RIBBON_MAIN`.

1. Importowanie bitmap do menu Plik, który jest dołączony do **aplikacji** przycisku.

   1. Importowanie pliku filesmall.bmp, który zawiera jedenaście 16 x 16 (16 x 176) obrazów. Zmień identyfikator mapy bitowej do `IDB_RIBBON_FILESMALL`.

   > [!NOTE]
   > Ponieważ potrzebujemy tylko obrazy pierwszych osiem 16 x 16 (16 x 128), może opcjonalnie przyciąć szerokość po prawej stronie tę mapę bitową z 176 do 128.

   1. Importowanie filelarge.bmp, który zawiera dziewięć 32 x 32 (32 x 288) obrazów. Zmień identyfikator mapy bitowej do `IDB_RIBBON_FILELARGE`.

1. Importuj mapy bitowe dla kategorii Wstążkę i panele. Każda karta w pasku wstążki jest kategorii i składa się z etykiety tekstu oraz opcjonalny obraz.

   1. Importuj bitową homesmall.bmp, która zawiera jedenaście 16 x 16 obrazy mapy bitowe małego przycisku. Zmień identyfikator mapy bitowej do `IDB_RIBBON_HOMESMALL`.

   1. Importuj bitową homelarge.bmp, która zawiera dziewięć 32 x 32 obrazy mapy bitowe dużych przycisków. Zmień identyfikator mapy bitowej do `IDB_RIBBON_HOMELARGE`.

1. Importuj bitmap do paneli wstążki o zmienionym rozmiarze. Te mapy bitowe lub ikony panelu są używane po operacji zmiany rozmiaru, jeśli Wstążka jest zbyt mała, aby wyświetlić całą panel.

   1. Importuj panelicons.bmp mapy bitowej, który zawiera osiem 16 x 16 obrazów. W **właściwości** okna **edytora mapy bitowej**, szerokość mapy bitowej do 64 (16 x 64). Zmień identyfikator mapy bitowej do `IDB_PANEL_ICONS`.

   > [!NOTE]
   > Ponieważ potrzebujemy tylko obrazy pierwsze cztery 16 x 16 (16 x 64), może opcjonalnie przyciąć szerokość po prawej stronie tej mapy bitowej od 128-64.

##  <a name="addribbon"></a> Dodawanie zasobu wstążki do projektu

Podczas konwersji aplikacji korzystającej z menu aplikacji korzystającej z wstążki, nie trzeba usunąć lub wyłączyć istniejące menu. Po prostu utwórz zasób wstążki, Dodaj przyciski wstążki, a następnie skojarzyć nowe przyciski z istniejących elementów menu. Mimo że menu nie są już widoczne, komunikaty z paska wstążki są przesyłane za pośrednictwem menu i menu skrótów w dalszym ciągu działać.

Wstążka składa się z **aplikacji** przycisku, który jest duży przycisk w lewym górnym rogu Wstążki i co najmniej jednej karty kategorii. Każda karta kategoria zawiera jeden lub więcej paneli, które działają jak kontenery dla przycisków Wstążki i kontrolek. Poniższa procedura pokazuje, jak utworzyć zasób wstążki, a następnie dostosować **aplikacji** przycisku.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Do dodawania zasobów wstążki do projektu

1. Za pomocą projektu bazgrołów wybranego w **Eksploratora rozwiązań**w **projektu** menu, kliknij przycisk **Dodaj zasób**.

1. W **Dodaj zasób** okno dialogowe, wybierz opcję **wstążki** a następnie kliknij przycisk **New**.

   Visual Studio tworzy zasób Wstążki i otwiera go w widoku Projekt. Identyfikator zasobu wstążki jest `IDR_RIBBON1`, która jest wyświetlana w **widok zasobów**. Wstążka zawiera jedną kategorię i jeden panel.

1. Można dostosować **aplikacji** przycisku, modyfikując jego właściwości. Identyfikatory komunikatów, które są używane w tym kodzie są już zdefiniowane w menu Bazgroły 1.0.

1. W widoku Projekt, kliknij przycisk **aplikacji** przycisk, aby wyświetlić jego właściwości. Zmień wartości właściwości w następujący sposób: **obraz** do `IDB_RIBBON_MAIN`, **monitu** do `File`, **klucze** do `f`, **duże obrazy** do `IDB_RIBBON_FILELARGE`, i **małe obrazy** do `IDB_RIBBON_FILESMALL`.

1. Wprowadzenie następujących modyfikacji utworzyć menu, który jest wyświetlany, gdy użytkownik kliknie **aplikacji** przycisku. Kliknij przycisk wielokropka (**...** ) obok pozycji **elementy główne** otworzyć **Edytor elementów**.

   1. Za pomocą **elementu** typu **przycisk** zaznaczone, kliknij przycisk **Dodaj** w celu dodania przycisku. Zmiana **podpis** do `&New`, **identyfikator** do `ID_FILE_NEW`, **obraz** do `0`, **duży obraz** do `0`.

   1. Kliknij przycisk **Dodaj** w celu dodania przycisku. Zmiana **podpis** do `&Save`, **identyfikator** do `ID_FILE_SAVE`, **obraz** do `2`, i **duży obraz** do `2`.

   1. Kliknij przycisk **Dodaj** w celu dodania przycisku. Zmiana **podpis** do `Save &As`, **identyfikator** do `ID_FILE_SAVE_AS`, **obraz** do `3`, i **duży obraz** do `3`.

   1. Kliknij przycisk **Dodaj** w celu dodania przycisku. Zmiana **podpis** do `&Print`, **identyfikator** do `ID_FILE_PRINT`, **obraz** do `4`, i **duży obraz** do `4`.

   1. Zmiana **elementu** typ **Separator** a następnie kliknij przycisk **Dodaj**.

   1. Zmiana **elementu** typ **przycisk**. Kliknij przycisk **Dodaj** do piątego przycisk Dodaj. Zmiana **podpis** do `&Close`, **identyfikator** do `ID_FILE_CLOSE`, **obraz** do `5`, i **duży obraz** do `5`.

1. Wprowadzenie następujących modyfikacji utworzyć podmenu w obszarze **drukowania** przycisk, który został utworzony w poprzednim kroku.

   1. Kliknij przycisk **drukowania** przycisk, zmień **elementu** typ **etykiety**, a następnie kliknij przycisk **Wstaw**. Zmiana **podpis** do `Preview and print the document`.

   1. Kliknij przycisk **drukowania** przycisk, zmień **elementu** typ **przycisk**i kliknij przycisk **Wstaw**. Zmiana **podpis** do `&Print`, **identyfikator** do `ID_FILE_PRINT`, **obraz** do `4`, i **duży obraz** do `4`.

   1. Kliknij przycisk **drukowania** przycisk, a następnie kliknij przycisk **Wstaw** w celu dodania przycisku. Zmiana **podpis** do `&Quick Print`, **identyfikator** do `ID_FILE_PRINT_DIRECT`, **obraz** do `7`, i **duży obraz** do `7`.

   1. Kliknij przycisk **drukowania** przycisk, a następnie kliknij przycisk **Wstaw** Aby dodać inny przycisk. Zmiana **podpis** do `Print Pre&view`, **identyfikator** do `ID_FILE_PRINT_PREVIEW`, **obraz** do `6`, i **duży obraz** do `6`.

   1. Teraz został zmodyfikowany **elementy główne**. Kliknij przycisk **Zamknij** aby zakończyć działanie **Edytor elementów**.

1. Po dokonaniu zmiany tworzy przycisk Zakończ, który pojawia się w dolnej części **aplikacji** przycisku menu.

   1. W **właściwości** okna, kliknij przycisk wielokropka (**...** ) obok pozycji **przycisk** otworzyć **Edytor elementów**.

   1. Za pomocą **elementu** typu **przycisk** zaznaczone, kliknij przycisk **Dodaj** w celu dodania przycisku. Zmiana **podpis** do `E&xit`, **identyfikator** do `ID_APP_EXIT`, **obraz** do `8`.

   1. Zmodyfikowano **przyciski**. Kliknij przycisk **Zamknij** aby zakończyć działanie **Edytor elementów**.

##  <a name="createinstance"></a> Tworzenie wystąpienia paska wstążki

Poniższe kroki pokazują jak utworzyć wystąpienie paska wstążki, podczas uruchamiania aplikacji. Aby dodać pasek wstążki do aplikacji, należy zadeklarować na Wstążce w pliku mainfrm.h. Następnie w pliku mainfrm.cpp, należy napisać kod ładowanie zasobu wstążki.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Aby utworzyć wystąpienie paska wstążki

1. W pliku mainfrm.h, Dodaj element członkowski danych do sekcji chronionych `CMainFrame`, definicji klasy dla głównej ramki. Ten element członkowski jest na Wstążce.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. W pliku mainfrm.cpp, Dodaj następujący kod przed końcowym znakiem `return` instrukcji na końcu `CMainFrame::OnCreate` funkcji. Tworzy wystąpienie paska wstążki.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a> Dostosowywanie zasób wstążki

Teraz, po utworzeniu **aplikacji** przycisku, można dodać elementów do wstążki.

> [!NOTE]
> W tym instruktażu wykorzystano ta sama ikona Panelu dla wszystkich paneli. Jednak można użyć innych indeksów listy obrazów do wyświetlania innymi ikonami.

### <a name="to-add-a-home-category-and-edit-panel"></a>Aby dodać kategorię głównej i edytować panelu

1. Program bazgrołów wymaga tylko jedną kategorię. W widoku Projekt w **przybornika**, kliknij dwukrotnie **kategorii** aby ją dodać i wyświetlić jego właściwości. Zmień wartości właściwości w następujący sposób: **podpis** do `&Home`, **duże obrazy** do `IDB_RIBBON_HOMELARGE`, **małe obrazy** do `IDB_RIBBON_HOMESMALL`.

1. Każda kategoria wstążki jest podzielony na nazwanej paneli. Każdy panel zawiera zestaw kontrolek tego pełną powiązanych operacji. Ta kategoria zawiera jeden panel. Kliknij przycisk **panelu**, a następnie zmień **podpis** do `Edit`.

1. Aby **Edytuj** panelu, Dodaj przycisk odpowiedzialny za czyszczenie zawartości dokumentu. Identyfikator komunikatu dla tego przycisku został już zdefiniowany w `IDR_SCRIBBTYPE` zasobu menu. Określ `Clear All` jako tekst przycisku i indeks mapy bitowej, która rozszerza przycisku. Otwórz **przybornika**, a następnie przeciągnij **przycisk** do **Edytuj** panelu. Kliknij przycisk, a następnie zmień **podpis** do `Clear All`, **identyfikator** do `ID_EDIT_CLEAR_ALL`, **indeks obrazu** do `0`, **duży indeks obrazu**  do `0`.

1. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Powinien zostać wyświetlony aplikacji bazgrołów, a powinien mieć paska wstążki w górnej części okna, a nie paska menu. Na Wstążce powinna mieć jedną kategorię **Home**, i **Home** powinien mieć jeden panel **Edytuj**. Przyciski wstążki, które dodano powinna być skojarzona z istniejących programów obsługi zdarzeń i **Otwórz**, **Zamknij**, **Zapisz**, **drukowania**, i **Wyczyść wszystko** przyciski powinny działać zgodnie z oczekiwaniami.

##  <a name="setlook"></a> Ustawienie wygląd aplikacji

A *visual Menedżera* jest obiekt globalny, który kontroluje wszystkie rysunku dla aplikacji. Ponieważ oryginalnej aplikacji bazgrołów używa styl interfejsu użytkownika pakietu Office 2000, aplikacja może wyglądać stosowane. Możesz zresetować aplikacji tak, aby wyglądała jak aplikacja pakietu Office 2007 za pomocą Menedżera visual Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Aby ustawić wygląd aplikacji

1. W `CMainFrame::OnCreate` funkcji, wpisz następujący kod przed `return 0;` instrukcję, aby zmienić domyślnego menedżera wizualnych i styl.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Aplikacja interfejsu użytkownika powinna być podobna interfejsu użytkownika pakietu Office 2007.

## <a name="next-steps"></a>Następne kroki

Zmodyfikowano klasycznego próbki Bazgroły MFC 1.0 do użycia **projektanta wstążki**. Teraz przejdź do [część 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Zobacz też

[Przewodniki](../mfc/walkthroughs-mfc.md)<br/>
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
