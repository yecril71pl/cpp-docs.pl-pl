---
title: 'Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 1) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: ce50d2c70107b4c88f223e32fdd8cc083df38840
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685548"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Wskazówki: Aktualizowanie aplikacji bazgrołów MFC (część 1)

W tym instruktażu pokazano, jak zmodyfikować istniejącą aplikację MFC przy użyciu interfejsu użytkownika wstążki. Program Visual Studio obsługuje zarówno wstążki pakietu Office 2007, jak i Windows 7 scen wstążki. Aby uzyskać więcej informacji na temat interfejsu użytkownika wstążki, zobacz [wstążek](/windows/desktop/uxguide/cmd-ribbons).

W tym przewodniku modyfikuje klasyczny przykład klasa Scribble MFC 1.0, który pozwala tworzyć rysunki wiersza za pomocą myszy. Tej części instruktażu pokazano, jak zmodyfikować próbki Bazgroły, tak, aby wyświetlał paska wstążki. [Część 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) dodaje więcej przycisków do paska wstążki.

## <a name="prerequisites"></a>Wymagania wstępne

[Przykłady Visual C++](../visual-cpp-samples.md)

[Przykłady Visual C++](../visual-cpp-samples.md)

##  <a name="top"></a> Sekcje

Ta część przewodnika zawiera następujące sekcje:

- [Zastąpienie klas bazowych](#replaceclass)

- [Dodawanie bitmap do projektu](#addbitmap)

- [Dodawanie zasobu wstążki do projektu](#addribbon)

- [Tworzenie wystąpienia paska wstążki](#createinstance)

- [Dodawanie kategorii wstążki](#addcategory)

- [Ustawienie wygląd aplikacji](#setlook)

##  <a name="replaceclass"></a> Zastąpienie klas bazowych

Aby przekonwertować aplikacji, która obsługuje menu do aplikacji, która obsługuje wstążki, musi pochodzić klasy narzędzi aplikacji, ramki okna i zaktualizowano klas podstawowych. (Zaleca się, możesz nie modyfikować oryginalnej próbki Bazgroły; zamiast tego należy wyczyścić projektu Bazgroły, skopiuj go do innego katalogu, a następnie zmodyfikuj kopii.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Zastąpienie klas bazowych w aplikacji bazgrołów

1. W scribble.cpp, upewnij się, że `CScribbleApp::InitInstance` zawiera wywołanie [afxoleinit —](../mfc/reference/ole-initialization.md#afxoleinit).

2. Dodaj następujący kod do pliku stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

3. W scribble.h, należy zmodyfikować definicję dla `CScribbleApp` klasy tak, aby go jest tworzony na podstawie [klasa CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

4. Bazgrołów 1.0 zostały zapisane, gdy aplikacje systemu Windows używane plik inicjujący (.ini) w celu zapisywania danych preferencji użytkownika. Zamiast pliku inicjującego zmodyfikować bazgrołów do przechowywania preferencji użytkownika w rejestrze. Aby ustawić klucz rejestru i podstawowa, wpisz następujący kod w `CScribbleApp::InitInstance` po `LoadStdProfileSettings()` instrukcji.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

5. Ramy głównej dla wielu aplikacji interfejsu (MDI) dokumentu nie jest już jest tworzony na podstawie `CMDIFrameWnd` klasy. Zamiast tego jest pochodną [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) klasy.

     W plikach mainfrm.h i mainfrm.cpp, Zastąp wszystkie odwołania do `CMDIFrameWnd` z `CMDIFrameWndEx`.

6. W plikach childfrm.h i childfrm.cpp, Zastąp `CMDIChildWnd` z `CMDIChildWndEx`.

     W childfrm. Plik h, Zastąp `CSplitterWnd` z `CSplitterWndEx`.

7. Zmodyfikuj paski narzędzi i stanu używać nowych klas MFC.

     W pliku mainfrm.h:

    1. Zastąp `CToolBar` z `CMFCToolBar`.

    2. Zastąp `CStatusBar` z `CMFCStatusBar`.

8. W pliku mainfrm.cpp:

    1. Zastąp `m_wndToolBar.SetBarStyle` z `m_wndToolBar.SetPaneStyle`

    2. Zastąp `m_wndToolBar.GetBarStyle` z `m_wndToolBar.GetPaneStyle`

    3. Zastąp `DockControlBar(&m_wndToolBar)` z `DockPane(&m_wndToolBar)`

9. W pliku ipframe.cpp komentarz następujące trzy wiersze kodu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

10. Jeśli zamierzasz Połącz swoją aplikację, statycznie, Dodaj następujący kod na początku projektu pliku zasobów (.rc).

    ```cpp
    #include "afxribbon.rc"
    ```

     Plik afxribbon.rc zawiera zasoby, które są wymagane w czasie wykonywania. [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) automatycznie dołącza ten plik podczas tworzenia aplikacji.

11. Zapisz zmiany, a następnie tworzenie i uruchamianie aplikacji.

[[Sekcje](#top)]

##  <a name="addbitmap"></a> Dodawanie bitmap do projektu

Czterech kolejnych krokach w tym przewodniku wymaga zasobów mapy bitowej. Możesz uzyskać odpowiednie map bitowych na różne sposoby:

- Użyj [edytory zasobów](../windows/resource-editors.md) wymyślaniem własne map bitowych. Lub użyj edytory zasobów można złożyć mapy bitowej przy użyciu obrazów graphics (PNG) sieci przenośnych, które są dołączone do programu Visual Studio. Obrazy te znajdują się w `VS2008ImageLibrary` katalogu.

     Ze Wstążki wymaga jednak, że niektóre mapy bitowe obsługują obrazy przezroczyste. Bitmapy przezroczyste użyć 32-bitowych pikseli, gdzie 24 bity Określ składników czerwonego, zielonego i niebieskiego koloru i zdefiniuj 8 bitów *kanał alfa* , który określa Przezroczystość koloru. Bieżący edytory zasobów można wyświetlić, ale nie modyfikować bitmapy z 32-bitowych pikseli. W związku z tym użyj edytora zewnętrznego zamiast edytory zasobów do manipulowania mapy bitowe przezroczysty.

- Skopiuj plik odpowiedni zasób z innej aplikacji do projektu, a następnie zaimportuj map bitowych z tego pliku.

W tym przewodniku kopiuje pliki zasobów z aplikacji w katalogu przykładów.

### <a name="to-add-bitmaps-to-the-project"></a>Dodawanie bitmap do projektu

1. Skopiuj następujące pliki .bmp z katalogu zasobów za pomocą Eksploratora plików (`res`) w próbce RibbonGadgets:

   1. Skopiuj main.bmp bazgrołów projektu.

   2. Skopiuj filesmall.bmp i filelarge.bmp do projektu bazgrołów.

   3. Utwórz nowe kopie plików filelarge.bmp i filesmall.bmp, ale zapisywać kopie w przykładzie RibbonGadgets. Zmień nazwę kopii homesmall.bmp i homelarge.bmp, a następnie przenieść kopie bazgrołów projektu.

   4. Utwórz kopię pliku toolbar.bmp, ale zapisać kopię w przykład RibbonGadgets. Zmień nazwę panelicons.bmp kopiowania, a następnie przenieś kopiowania do projektu bazgrołów.

2. Importuj mapy bitowej dla aplikacji MFC. W **widok zasobów**, kliknij dwukrotnie **scribble.rc** węzła, kliknij dwukrotnie **mapy bitowej** węzłem, a następnie kliknij przycisk **Dodaj zasób**. W oknie dialogowym kliknij **importu**. Przejdź do `res` katalogu, wybierz plik main.bmp, a następnie kliknij przycisk **Otwórz**.

   Mapa bitowa main.bmp zawiera obraz 26 x 26. Zmień identyfikator mapy bitowej na IDB_RIBBON_MAIN.

3. Importuj bitmap do menu Plik, który jest dołączony do przycisku aplikacji.

   1. Importowanie pliku filesmall.bmp, który zawiera dziesięć 16 x 16 (16 x 160) obrazów. Ponieważ potrzebujemy obrazy tylko osiem 16 x 16 (16 x 128), należy użyć **widok zasobów** zmienić szerokość tej mapy bitowej z 160-128. Zmień identyfikator mapy bitowej na IDB_RIBBON_FILESMALL.

   2. Importowanie filelarge.bmp, który zawiera osiem 32 x 32 (32 x 256) obrazów. Zmień identyfikator mapy bitowej na IDB_RIBBON_FILELARGE.

4. Importuj mapy bitowe dla kategorii Wstążkę i panele. Każda karta w pasku wstążki jest kategorii i składa się z etykiety tekstu oraz opcjonalny obraz.

   1. Importuj bitową homesmall.bmp, która zawiera osiem 16 x 16 obrazy mapy bitowe małego przycisku. Zmień identyfikator mapy bitowej na IDB_RIBBON_HOMESMALL.

   2. Importuj bitową homelarge.bmp, która zawiera osiem 32 x 32 obrazy mapy bitowe dużych przycisków. Zmień identyfikator mapy bitowej na IDB_RIBBON_HOMELARGE.

5. Importuj bitmap do paneli wstążki o zmienionym rozmiarze. Te mapy bitowe lub ikony panelu są używane po operacji zmiany rozmiaru, jeśli Wstążka jest zbyt mała, aby wyświetlić całą panel.

   1. Importuj panelicons.bmp mapy bitowej, który zawiera osiem 16 x 16 obrazów. W **właściwości** okna **edytora mapy bitowej**, szerokość mapy bitowej do 64 (16 x 64). Zmień identyfikator mapy bitowej na IDB_PANEL_ICONS.

[[Sekcje](#top)]

##  <a name="addribbon"></a> Dodawanie zasobu wstążki do projektu

Podczas konwersji aplikacji korzystającej z menu aplikacji korzystającej z wstążki, trzeba usunąć lub wyłączyć istniejące menu. Zamiast tego należy utworzyć zasób wstążki, Dodaj przyciski Wstążki i skojarz nowe przyciski z istniejących elementów menu. Mimo że menu nie są już widoczne, wiadomości na Wstążce są przesyłane za pośrednictwem menu. Ponadto menu, skróty nadal działać.

Wstążka składa się z przycisku aplikacji, która jest duży przycisk w lewym górnym rogu wstążki, i co najmniej jednej karty kategorii. Każda karta kategoria zawiera jeden lub więcej paneli, które działają jak kontenery dla przycisków Wstążki i kontrolek. Poniższa procedura pokazuje, jak utworzyć zasób wstążki, a następnie dostosować przycisku aplikacji.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Do dodawania zasobów wstążki do projektu

1. Na **projektu** menu, kliknij przycisk **Dodaj zasób**.

2. W **Dodaj zasób** okno dialogowe, wybierz opcję **wstążki** a następnie kliknij przycisk **New**.

   Visual Studio tworzy zasób Wstążki i otwiera go w widoku Projekt. Identyfikator zasobu wstążki jest IDR_RIBBON1, która jest wyświetlana w **widok zasobów**. Wstążka zawiera jedną kategorię i jeden panel.

3. Przycisk aplikacji można dostosować, modyfikując jego właściwości. Identyfikatory komunikatów, które są używane w tym kodzie są już zdefiniowane w menu Bazgroły 1.0.

4. W widoku Projekt kliknij przycisk aplikacji, aby wyświetlić jego właściwości. Zmień wartości właściwości w następujący sposób: **obraz** do `IDB_RIBBON_MAIN`, **monitu** do `File`, **klucze** do `f`, **duże obrazy** do `IDB_RIBBON_FILELARGE`, i **małe obrazy** do `IDB_RIBBON_FILESMALL`.

5. Wprowadzenie następujących modyfikacji utworzyć menu, który jest wyświetlany, gdy użytkownik kliknie przycisk aplikacji. Kliknij przycisk wielokropka (**...** ) obok pozycji **elementy główne** otworzyć **Edytor elementów**.

   1. Kliknij przycisk **Dodaj** w celu dodania przycisku. Zmiana **podpis** do `&New`, **identyfikator** do `ID_FILE_NEW`, **obraz** do `0`, **duży obraz** do `0`.

   2. Kliknij przycisk **Dodaj** można dodać drugi przycisk. Zmiana **podpis** do `&Save`, **identyfikator** do `ID_FILE_SAVE`, **obraz** do `2`, i **duży obraz** do `2`.

   3. Kliknij przycisk **Dodaj** dodać trzeci przycisk. Zmiana **podpis** do `Save &As`, **identyfikator** do `ID_FILE_SAVE_AS`, **obraz** do `3`, i **duży obraz** do `3`.

   4. Kliknij przycisk **Dodaj** do czwartej przycisk Dodaj. Zmiana **podpis** do `&Print`, **identyfikator** do `ID_FILE_PRINT`, **obraz** do `4`, i **duży obraz** do `4`.

   5. Zmiana **elementu** typ **Separator** a następnie kliknij przycisk **Dodaj**.

   6. Zmiana **elementu** typ **przycisk**. Kliknij przycisk **Dodaj** do piątego przycisk Dodaj. Zmiana **podpis** do `&Close`, **identyfikator** do `ID_FILE_CLOSE`, **obraz** do `5`, i **duży obraz** do `5`.

6. Wprowadzenie następujących modyfikacji utworzyć podmenu w obszarze przycisku Drukuj, który został utworzony w poprzednim kroku.

   1. Kliknij przycisk **drukowania** przycisk, zmień **elementu** typ **etykiety**, a następnie kliknij przycisk **Wstaw**. Zmiana **podpis** do `Preview and print the document`.

   2. Kliknij przycisk **drukowania** przycisk, zmień **elementu** typ **przycisk**i kliknij przycisk **Wstaw**. Zmiana **podpis** do `&Print`, **identyfikator** do `ID_FILE_PRINT`, **obraz** do `4`, i **duży obraz** do `4`.

   3. Kliknij przycisk **drukowania** przycisk, a następnie kliknij przycisk **Wstaw** w celu dodania przycisku. Zmiana **podpis** do `&Quick Print`, **identyfikator** do `ID_FILE_PRINT_DIRECT`, **obraz** do `7`, i **duży obraz** do `7`.

   4. Kliknij przycisk **drukowania** przycisk, a następnie kliknij przycisk **Wstaw** Aby dodać inny przycisk. Zmiana **podpis** do `Print Pre&view`, **identyfikator** do `ID_FILE_PRINT_PREVIEW`, **obraz** do `6`, i **duży obraz** do `6`.

   5. Teraz zmodyfikowano **elementy główne**. Kliknij przycisk **Zamknij** aby zakończyć działanie **Edytor elementów**.

7. Po dokonaniu zmiany tworzy przycisk Zakończ, który pojawia się u dołu menu przycisku aplikacji.

   1. W **właściwości** okna, kliknij przycisk wielokropka (**...** ) obok pozycji **przycisk** otworzyć **Edytor elementów**.

   2. Kliknij przycisk **Dodaj** w celu dodania przycisku. Zmiana **podpis** do `E&xit`, **identyfikator** do `ID_APP_EXIT`, **obraz** do `8`.

[[Sekcje](#top)]

##  <a name="createinstance"></a> Tworzenie wystąpienia paska wstążki

Poniższe kroki pokazują jak utworzyć wystąpienie paska wstążki, podczas uruchamiania aplikacji. Aby dodać pasek wstążki do aplikacji, należy zadeklarować na Wstążce w pliku mainfrm.h. Następnie w pliku mainfrm.cpp, należy napisać kod ładowanie zasobu wstążki.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Aby utworzyć wystąpienie paska wstążki

1. W pliku mainfrm.h, Dodaj element członkowski danych do sekcji chronionych `CMainFrame`, definicji klasy dla głównej ramki. Ten element członkowski reprezentuje paska wstążki.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. W pliku mainfrm.cpp, Dodaj następujący kod przed końcowym znakiem `return` instrukcji na końcu `CMainFrame::OnCreate` funkcji. Spowoduje to utworzenie wystąpienia paska wstążki.

    ```cpp
    // Create the ribbon bar
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
> W tym instruktażu wykorzystano ta sama ikona Panelu dla wszystkich paneli. Jednak można użyć innych indeksów listy obrazów do wyświetlania innymi ikonami.

### <a name="to-add-a-home-category-and-edit-panel"></a>Aby dodać kategorię głównej i edytować panelu

1. Program bazgrołów wymaga tylko jedną kategorię. W widoku Projekt, kliknij przycisk **kategorii** Aby wyświetlić jego właściwości. Zmień wartości właściwości w następujący sposób: **podpis** do `&Home`, **duże obrazy** do `IDB_RIBBON_HOMELARGE`, **małe obrazy** do `IDB_RIBBON_HOMESMALL`.

2. Każda kategoria wstążki jest podzielony na nazwanej paneli. Każdy panel zawiera zestaw kontrolek, które wykonują operacje powiązane. Ta kategoria zawiera jeden panel. Kliknij przycisk **panelu**, a następnie zmień **podpis** do `Edit` i **indeks obrazu** do `0`.

3. Aby **Edytuj** panelu, Dodaj przycisk, który jest odpowiedzialny za czyszczenie zawartości dokumentu. Identyfikator komunikatu dla tego przycisku został już zdefiniowany w zasobie menu IDR_SCRIBBTYPE. Określ `Clear All` jako tekst przycisku i indeks mapy bitowej, która rozszerza przycisku. Otwórz **przybornika**, a następnie przeciągnij **przycisk** do **Edytuj** panelu. Kliknij przycisk, a następnie zmień **podpis** do `Clear All`, **identyfikator** do `ID_EDIT_CLEAR_ALL`, **indeks obrazu** do `0`, **duży indeks obrazu**  do `0`.

4. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Powinien zostać wyświetlony aplikacji bazgrołów, a powinien mieć paska wstążki w górnej części okna, a nie paska menu. Na Wstążce powinna mieć jedną kategorię **Home**, i **Home** powinien mieć jeden panel **Edytuj**. Przyciski wstążki, które dodano powinna być skojarzona z istniejących programów obsługi zdarzeń i **Otwórz**, **Zamknij**, **Zapisz**, **drukowania**, i **Wyczyść wszystko** przyciski powinny działać zgodnie z oczekiwaniami.

[[Sekcje](#top)]

##  <a name="setlook"></a> Ustawienie wygląd aplikacji

A *visual Menedżera* jest obiekt globalny, który kontroluje wszystkie rysunku dla aplikacji. Ponieważ oryginalnej aplikacji bazgrołów używa styl interfejsu użytkownika pakietu Office 2000, aplikacja może wyglądać stosowane. Możesz zresetować aplikacji tak, aby wyglądała jak aplikacja pakietu Office 2007 za pomocą Menedżera visual Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Aby ustawić wygląd aplikacji

1. W `CMainFrame::OnCreate` funkcji, wpisz następujący kod, aby zmienić domyślnego menedżera wizualnych i styl.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

2. Zapisz zmiany i następnie, skompiluj i uruchom aplikację. Aplikacja interfejsu użytkownika powinna być podobna interfejsu użytkownika pakietu Office 2007.

[[Sekcje](#top)]

## <a name="next-steps"></a>Następne kroki

Zmodyfikowano klasycznego próbki Bazgroły MFC 1.0, aby używać projektanta wstążki. Teraz przejdź do [część 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)  
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 2)] (.. / mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)  
