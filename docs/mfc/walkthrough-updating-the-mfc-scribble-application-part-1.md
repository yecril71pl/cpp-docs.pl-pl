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
ms.openlocfilehash: 18803d2222c80b80ac2b1fde75b442ea1e9a89bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360258"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 1)

W tym przewodniku pokazano, jak zmodyfikować istniejącą aplikację MFC, aby użyć interfejsu użytkownika Wstążki. Program Visual Studio obsługuje wstążkę pakietu Office 2007 i scenotyczną wstążkę systemu Windows 7. Aby uzyskać więcej informacji na temat interfejsu użytkownika Wstążki, zobacz [Wstążki](/windows/win32/uxguide/cmd-ribbons).

W tym instruktażu modyfikuje klasyczny bazgroły 1.0 MFC próbki, która umożliwia użycie myszy do tworzenia rysunków linii. W tej części przewodnika pokazano, jak zmodyfikować przykład bazgroły, tak aby wyświetlał pasek wstążki. [Część 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) dodaje więcej przycisków do paska wstążki.

## <a name="prerequisites"></a>Wymagania wstępne

[Próbka Bazgrołów 1.0 MFC](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Aby uzyskać pomoc dotyczącą konwersji do programu Visual Studio 2017 lub nowszej, zobacz [Przewodnik po portowaniu: Bazgroły MFC](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a>Sekcje

Ta część przewodnika zawiera następujące sekcje:

- [Zastępowanie klas podstawowych](#replaceclass)

- [Dodawanie map bitowych do projektu](#addbitmap)

- [Dodawanie zasobu wstążki do projektu](#addribbon)

- [Tworzenie wystąpienia paska wstążki](#createinstance)

- [Dodawanie kategorii wstążki](#addcategory)

- [Ustawianie wyglądu aplikacji](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>Zastępowanie klas podstawowych

Aby przekonwertować aplikację, która obsługuje menu do aplikacji, która obsługuje wstążkę, należy wyprowadzić klasy aplikacji, ramki i paska narzędzi ze zaktualizowanych klas podstawowych. (Sugerujemy, aby nie modyfikować oryginalnej próbki bazgrołów. Zamiast tego wyczyść projekt Bazgroły, skopiuj go do innego katalogu, a następnie zmodyfikuj kopię).

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Aby zastąpić klasy podstawowe w aplikacji Bazgroły

1. W pliku scribble.cpp `CScribbleApp::InitInstance` sprawdź, czy zawiera połączenie z [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Dodaj następujący kod do pliku *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych):

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. W pliku scribble.h zmodyfikuj definicję `CScribbleApp` klasy tak, aby pochodziła z klasy [CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Bazgroły 1.0 został napisany, gdy aplikacje systemu Windows używane inicjowania (.ini) plik do zapisywania danych preferencji użytkownika. Zamiast pliku inicjowania zmodyfikuj bazgroły, aby przechowywać preferencje użytkownika w rejestrze. Aby ustawić klucz rejestru i podstawową, `CScribbleApp::InitInstance` wpisz `LoadStdProfileSettings()` następujący kod w po instrukcji.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Ramka główna aplikacji interfejsu wielu dokumentów (MDI) nie `CMDIFrameWnd` jest już pochodną klasy. Zamiast tego jest pochodną [cmdiFrameWndEx](../mfc/reference/cmdiframewndex-class.md) klasy.

    W plikach mainfrm.h i mainfrm.cpp zastąp wszystkie odniesienia do `CMDIFrameWnd` pliku `CMDIFrameWndEx`.

1. W plikach childfrm.h i childfrm.cpp zastąp `CMDIChildWnd` `CMDIChildWndEx`.

    W childfrm. h, zastąp `CSplitterWnd` na `CSplitterWndEx`.

1. Zmodyfikuj paski narzędzi i paski stanu, aby użyć nowych klas MFC.

    W pliku mainfrm.h:

    1. Zastąp element `CToolBar` pytaniem `CMFCToolBar`.

    1. Zastąp element `CStatusBar` pytaniem `CMFCStatusBar`.

1. W pliku mainfrm.cpp:

    1. Zamień `m_wndToolBar.SetBarStyle` na`m_wndToolBar.SetPaneStyle`

    1. Zamień `m_wndToolBar.GetBarStyle` na`m_wndToolBar.GetPaneStyle`

    1. Zamień `DockControlBar(&m_wndToolBar)` na`DockPane(&m_wndToolBar)`

1. W pliku ipframe.cpp wykomentuj następujące trzy wiersze kodu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>Dodawanie map bitowych do projektu

Następne cztery kroki tego przewodnika wymagają zasobów mapy bitowej. Odpowiednie mapy bitowe można uzyskać na różne sposoby:

- [Edytory zasobów](../windows/resource-editors.md) można wymyślać własne mapy bitowe. Możesz też użyć edytorów zasobów do zmontowania map bitowych z obrazów przenośnej grafiki sieciowej (png), które są dołączone do programu Visual Studio i można je pobrać z [biblioteki obrazów programu Visual Studio.](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)

    Jednak interfejs użytkownika **Wstążki** wymaga, aby niektóre mapy bitowe obsługiwać przezroczyste obrazy. Przezroczyste mapy bitowe używają 32-bitowych pikseli, w których 24 bity określają czerwone, zielone i niebieskie składniki koloru, a 8 bitów definiuje *kanał alfa* określający przezroczystość koloru. Bieżące edytory zasobów mogą wyświetlać, ale nie modyfikować map bitowych za pomocą pikseli 32-bitowych. W związku z tym należy użyć zewnętrznego edytora obrazów zamiast edytorów zasobów do manipulowania przezroczystymi mapami bitowymi.

- Skopiuj odpowiedni plik zasobów z innej aplikacji do projektu, a następnie zaimportuj mapy bitowe z tego pliku.

Ten instruktaż kopiuje pliki zasobów z przykładu utworzonego w [przewodniku: Tworzenie aplikacji wstążki przy użyciu MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Aby dodać mapy bitowe do projektu

1. Eksplorator plików służy do kopiowania następujących plików`res`bmp z katalogu zasobów (`res`) przykładu Wstążki do katalogu zasobów ( ) projektu Bazgroły:

   1. Skopiuj plik main.bmp do projektu bazgrołów.

   1. Skopiuj plik filesmall.bmp i filelarge.bmp do projektu Bazgroły.

   1. Dawać nowy kopie ten filelarge.bmp i filesmall.bmp akta, oprócz zapis ten kopie w ten Wstążka przykład. Zmień nazwę kopii homesmall.bmp i homelarge.bmp, a następnie przenieś kopie do projektu Bazgroły.

   1. Zrób kopię pliku toolbar.bmp, ale zapisz ją w przykładzie Wstążki. Zmień nazwę pliku copy panelicons.bmp, a następnie przenieś kopię do projektu bazgrołów.

1. Zaimportuj mapę bitową dla aplikacji MFC. W **widoku zasobu**kliknij dwukrotnie węzeł **scribble.rc,** kliknij dwukrotnie węzeł **Mapy bitowej,** a następnie kliknij pozycję **Dodaj zasób**. W wyświetlonym oknie dialogowym kliknij pozycję **Importuj**. Przejdź do `res` katalogu, wybierz plik main.bmp, a następnie kliknij przycisk **Otwórz**.

   Mapa bitowa main.bmp zawiera obraz o rysy 26x26. Zmień identyfikator mapy bitowej `IDB_RIBBON_MAIN`na .

1. Zaimportuj mapy bitowe dla menu pliku dołączonego do przycisku **Aplikacja.**

   1. Importuj plik filesmall.bmp, który zawiera jedenaście obrazów 16x16 (16x176). Zmień identyfikator mapy bitowej `IDB_RIBBON_FILESMALL`na .

   > [!NOTE]
   > Ponieważ potrzebujemy tylko pierwszych ośmiu obrazów 16x16 (16x128), opcjonalnie można przyciąć szerokość tej mapy bitowej po prawej stronie od 176 do 128.

   1. Importuj pliklarge.bmp, który zawiera dziewięć obrazów 32x32 (32x288). Zmień identyfikator mapy bitowej `IDB_RIBBON_FILELARGE`na .

1. Importowanie map bitowych dla kategorii i paneli wstążki. Każda karta na pasku wstążki jest kategorią i składa się z etykiety tekstowej i obrazu opcjonalnego.

   1. Importuj mapę bitową homesmall.bmp, która zawiera jedenaście obrazów 16x16 dla małych map bitowych przycisków. Zmień identyfikator mapy bitowej `IDB_RIBBON_HOMESMALL`na .

   1. Importuj mapę bitową homelarge.bmp, która zawiera dziewięć obrazów 32x32 dla dużych map bitowych przycisków. Zmień identyfikator mapy bitowej `IDB_RIBBON_HOMELARGE`na .

1. Importowanie map bitowych dla paneli wstążki o przekątnych ominie. Te mapy bitowe lub ikony panelu są używane po operacji zmiany rozmiaru, jeśli wstążka jest zbyt mała, aby wyświetlić cały panel.

   1. Importuj mapę bitową panelicons.bmp, która zawiera osiem obrazów 16x16. W oknie **Właściwości** **Edytora bitmap**dostosuj szerokość mapy bitowej do 64 (16x64). Zmień identyfikator mapy bitowej `IDB_PANEL_ICONS`na .

   > [!NOTE]
   > Ponieważ potrzebujemy tylko pierwszych czterech obrazów 16x16 (16x64), opcjonalnie można przyciąć szerokość prawej strony tej mapy bitowej od 128 do 64.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>Dodawanie zasobu wstążki do projektu

Podczas konwertowania aplikacji, która używa menu do aplikacji, która używa wstążki, nie trzeba usuwać ani wyłączać istniejących menu. Wystarczy utworzyć zasób wstążki, dodać przyciski wstążki, a następnie skojarzyć nowe przyciski z istniejącymi elementami menu. Mimo że menu nie są już widoczne, wiadomości z paska wstążki są kierowane przez menu, a skróty menu nadal działają.

Wstążka składa się z przycisku **Aplikacja,** który jest dużym przyciskiem w lewym górnym rogu wstążki i jednej lub kilku kart kategorii. Każda karta kategorii zawiera jeden lub więcej paneli, które działają jako kontenery dla przycisków wstążki i formantów. W poniższej procedurze pokazano, jak utworzyć zasób wstążki, a następnie dostosować przycisk **Aplikacji.**

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Aby dodać zasób wstążki do projektu

1. Po wybraniu projektu Bazgroły w **Eksploratorze rozwiązań**w menu **Projekt** kliknij polecenie **Dodaj zasób**.

1. W oknie dialogowym **Dodawanie zasobu** wybierz **wstążkę,** a następnie kliknij pozycję **Nowy**.

   Program Visual Studio tworzy zasób wstążki i otwiera go w widoku projektu. Identyfikator zasobu wstążki jest `IDR_RIBBON1`wyświetlany w widoku **zasobu**. Wstążka zawiera jedną kategorię i jeden panel.

1. Przycisk **Aplikacji** można dostosować, modyfikując jego właściwości. Identyfikatory wiadomości, które są używane w tym kodzie są już zdefiniowane w menu bazgrołów 1.0.

1. W widoku projektu kliknij przycisk **Aplikacja,** aby wyświetlić jego właściwości. Zmień wartości właściwości **Image** w `IDB_RIBBON_MAIN`następujący sposób: Obraz `f`na , **Monituj** do `File`, **Klawisze** do , **Duże obrazy** do `IDB_RIBBON_FILELARGE`, i **Małe obrazy** do `IDB_RIBBON_FILESMALL`.

1. Następujące modyfikacje utworzyć menu, które pojawia się po kliknięciu przycisku **aplikacji.** Kliknij wielokropek (**...**) obok **pozycji Elementy główne,** aby otworzyć **Edytor elementów**.

   1. Po wybraniu **przycisku** Typ **elementu** kliknij przycisk **Dodaj,** aby dodać przycisk. Zmień **Caption** podpis `&New`na , `ID_FILE_NEW` **ID** , **Obraz** `0`na , **Duży obraz** do `0`.

   1. Kliknij **przycisk Dodaj,** aby dodać przycisk. Zmień **Caption** podpis `&Save`na , `ID_FILE_SAVE` **ID** , **Obraz** na `2`, i **Duży obraz** na `2`.

   1. Kliknij **przycisk Dodaj,** aby dodać przycisk. Zmień **Caption** podpis `Save &As`na , `ID_FILE_SAVE_AS` **ID** , **Obraz** na `3`, i **Duży obraz** na `3`.

   1. Kliknij **przycisk Dodaj,** aby dodać przycisk. Zmień **Caption** podpis `&Print`na , `ID_FILE_PRINT` **ID** , **Obraz** na `4`, i **Duży obraz** na `4`.

   1. Zmień typ elementu na **separator,** a następnie kliknij przycisk **Item** **Dodaj**.

   1. Zmień typ **elementu** na **przycisk**. Kliknij **przycisk Dodaj,** aby dodać piąty przycisk. Zmień **Caption** podpis `&Close`na , `ID_FILE_CLOSE` **ID** , **Obraz** na `5`, i **Duży obraz** na `5`.

1. Następujące modyfikacje tworzą podmenu pod przyciskiem **Drukuj** utworzony w poprzednim kroku.

   1. Kliknij przycisk **Drukuj,** zmień typ **elementu** na **Etykieta**, a następnie kliknij przycisk **Wstaw**. Zmień **Caption** podpis `Preview and print the document`na .

   1. Kliknij przycisk **Drukuj,** zmień typ **elementu** na **Przycisk**i kliknij pozycję **Wstaw**. Zmień **Caption** podpis `&Print`na , `ID_FILE_PRINT` **ID** , **Obraz** na `4`, i **Duży obraz** na `4`.

   1. Kliknij przycisk **Drukuj,** a następnie kliknij pozycję **Wstaw,** aby dodać przycisk. Zmień **Caption** podpis `&Quick Print`na , `ID_FILE_PRINT_DIRECT` **ID** , **Obraz** na `7`, i **Duży obraz** na `7`.

   1. Kliknij przycisk **Drukuj,** a następnie kliknij pozycję **Wstaw,** aby dodać kolejny przycisk. Zmień **Caption** podpis `Print Pre&view`na , `ID_FILE_PRINT_PREVIEW` **ID** , **Obraz** na `6`, i **Duży obraz** na `6`.

   1. Elementy **główne**zostały zmodyfikowane. Kliknij **przycisk Zamknij,** aby zamknąć **Edytor elementów**.

1. Następująca modyfikacja tworzy przycisk wyjścia, który pojawia się w dolnej części menu przycisku **aplikacji.**

   1. Wybierz kartę **Widok zasobów** w **Eksploratorze rozwiązań**.
   1. W oknie **Właściwości** kliknij wielokropek (**...**) obok **przycisku,** aby otworzyć **Edytor elementów**.

   1. Po wybraniu **przycisku** Typ **elementu** kliknij przycisk **Dodaj,** aby dodać przycisk. Zmień **Caption** podpis `E&xit`na , `ID_APP_EXIT` **ID** , **Obraz** na `8`.

   1. Zmodyfikowano **przyciski**. Kliknij **przycisk Zamknij,** aby zamknąć **Edytor elementów**.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>Tworzenie wystąpienia paska wstążki

Poniższe kroki pokazują, jak utworzyć wystąpienie paska wstążki po uruchomieniu aplikacji. Aby dodać pasek wstążki do aplikacji, zadeklaruj pasek wstążki w pliku mainfrm.h. Następnie w pliku mainfrm.cpp napisz kod, aby załadować zasób wstążki.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Aby utworzyć wystąpienie paska wstążki

1. W pliku mainfrm.h dodaj element członkowski danych `CMainFrame`do chronionej sekcji , definicji klasy dla ramki głównej. Ten element członkowski jest przeznaczony dla paska wstążki.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. W pliku mainfrm.cpp dodaj następujący kod `return` przed końcową instrukcją na końcu `CMainFrame::OnCreate` funkcji. Tworzy wystąpienie paska wstążki.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>Dostosowywanie zasobu wstążki

Po utworzeniu przycisku **Aplikacja** można dodać elementy do wstążki.

> [!NOTE]
> W tym instruktażu użyto tej samej ikony panelu dla wszystkich paneli. Można jednak użyć innych indeksów listy obrazów, aby wyświetlić inne ikony.

### <a name="to-add-a-home-category-and-edit-panel"></a>Aby dodać kategorię Dom i panel Edytuj

1. Program Bazgroły wymaga tylko jednej kategorii. W widoku projektu w **przyborniku**kliknij dwukrotnie **kategorię,** aby dodać jedną z nich i wyświetlić jego właściwości. Zmień wartości właściwości w `&Home`następujący sposób: `IDB_RIBBON_HOMELARGE` **Podpis** na `IDB_RIBBON_HOMESMALL`, Duże **obrazy** na , Małe **obrazy** na .

1. Każda kategoria wstążki jest zorganizowana w nazwane panele. Każdy panel zawiera zestaw formantów, które kończą powiązane operacje. Ta kategoria ma jeden panel. Kliknij **pozycję Panel**, a następnie zmień pozycję **Podpis** na `Edit`.

1. Do panelu **Edycja** dodaj przycisk odpowiedzialny za wyczyszczenie zawartości dokumentu. Identyfikator komunikatu dla tego przycisku został `IDR_SCRIBBTYPE` już zdefiniowany w zasobie menu. Określ `Clear All` jako tekst przycisku i indeks mapy bitowej, który ozdabia przycisk. Otwórz **przybornik**, a następnie przeciągnij **przycisk** do panelu **Edycja.** Kliknij przycisk, a **Caption** następnie `Clear All`zmień caption `ID_EDIT_CLEAR_ALL`na , **ID** , `0` **Indeks obrazu** do `0`, Duży indeks **obrazu** na .

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację. Aplikacja Bazgroły powinna być wyświetlana i powinna mieć pasek wstążki w górnej części okna zamiast paska menu. Pasek wstążki powinien mieć jedną kategorię, **Strona główna**i **Strona główna** powinny mieć jeden **panel, Edytuj**. Dodane przyciski wstążki powinny być skojarzone z istniejącymi programami obsługi zdarzeń, a przyciski **Otwórz,** **Zamknij,** **Zapisz,** **Drukuj**i **Wyczyść wszystkie** powinny działać zgodnie z oczekiwaniami.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>Ustawianie wyglądu aplikacji

*Menedżer wizualny* jest obiektem globalnym, który kontroluje cały rysunek dla aplikacji. Ponieważ oryginalna aplikacja Bazgroły używa stylu interfejsu użytkownika pakietu Office 2000, aplikacja może wyglądać staroświeckim. Możesz zresetować aplikację, aby użyć menedżera wizualnego pakietu Office 2007, tak aby przypominał aplikację pakietu Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Aby ustawić wygląd aplikacji

1. W `CMainFrame::OnCreate` funkcji wpisz następujący kod `return 0;` przed instrukcją, aby zmienić domyślny menedżer wizualny i styl.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Zapisz zmiany, a następnie skompiluj i uruchom aplikację. Interfejs użytkownika aplikacji powinien przypominać interfejs użytkownika pakietu Office 2007.

## <a name="next-steps"></a>Następne kroki

Zmodyfikowano klasyczną próbkę bazgrołów 1.0 MFC, aby użyć **projektanta wstążki**. Teraz przejdź do [części 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Zobacz też

[Wskazówki](../mfc/walkthroughs-mfc.md)<br/>
[Przewodnik: aktualizowanie aplikacji bazgrołów MFC (część 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
