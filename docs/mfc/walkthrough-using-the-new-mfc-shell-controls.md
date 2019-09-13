---
title: 'Przewodnik: Korzystanie z nowych formantów powłoki MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: cf0a6bd230364b48c78c72b8e453e7e641fb2d0e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907409"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Przewodnik: Korzystanie z nowych formantów powłoki MFC

W tym instruktażu utworzysz aplikację przypominającą Eksplorator plików. Utworzysz okno, które ma dwa okienka. W lewym okienku będzie przechowywany obiekt [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) , który wyświetla pulpit w widoku hierarchicznym. W okienku po prawej stronie zostanie umieszczona [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) , która będzie zawierać pliki w folderze wybranym w okienku po lewej stronie.

## <a name="prerequisites"></a>Wymagania wstępne

- W programie Visual Studio 2017 lub nowszym obsługa MFC jest składnikiem opcjonalnym. Aby go zainstalować, Otwórz Instalator programu Visual Studio z menu Start systemu Windows. Znajdź używaną wersję programu Visual Studio, a następnie wybierz przycisk **Modyfikuj** . Upewnij się, że jest zaznaczone pole **Programowanie na pulpicie z C++**  kafelkiem. W obszarze **Opcjonalne składniki**Sprawdź przycisk **Obsługa MFC** .

- W tym przewodniku przyjęto założenie, że program Visual Studio został skonfigurowany do używania **ogólnych ustawień deweloperskich**. Jeśli używasz innego ustawienia programistycznego, niektóre z okien programu Visual Studio, które są używane w tym instruktażu, mogą nie być wyświetlane domyślnie.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Aby utworzyć nową aplikację MFC przy użyciu Kreatora aplikacji MFC

Kroki te różnią się w zależności od używanej wersji programu Visual Studio. Upewnij się, że selektor wersji w lewym górnym rogu tej strony jest poprawnie ustawiony.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Aby utworzyć projekt MFC w programie Visual Studio 2019

1. Z menu głównego wybierz pozycję **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Tworzenie nowego projektu** .

1. W polu wyszukiwania w górnej części wpisz **MFC** , a następnie wybierz pozycję **aplikacja MFC** z listy wyników. 

1. Kliknij przycisk **Dalej**. Na następnej stronie Wprowadź nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

   Po wyświetleniu **Kreatora aplikacji MFC** należy użyć następujących opcji:
 
   1. Wybierz pozycję **Typ aplikacji** po lewej stronie. Następnie wybierz pozycję **pojedynczy dokument** , a następnie wybierz pozycję **dokument/widok obsługa architektury**. W obszarze **styl projektu**wybierz pozycję **Visual Studio**, a następnie z listy rozwijanej **styl i kolory wizualizacji** wybierz pozycję **Office 2007 (motyw niebieski)** .

   1. W okienku **Obsługa dokumentu złożonego** zaznacz opcję **Brak**.

   1. Nie wprowadzaj żadnych zmian w okienku **Właściwości szablonu dokumentu** .

   1. W okienku **funkcje interfejsu użytkownika** upewnij się, że jest zaznaczona opcja **Użyj paska menu i paska narzędzi** . Pozostaw wszystkie inne opcje.

   1. W okienku **funkcje zaawansowane** wybierz opcję **formanty ActiveX**, **manifest formantów wspólnych**i **okienko nawigacji** . Pozostaw wszystkie inne elementy. Opcja **okienka nawigacji** spowoduje, że Kreator utworzy okienko z lewej strony okna z `CMFCShellTreeCtrl` już osadzonym.

   1. Nie będziemy wprowadzać żadnych zmian w okienku **wygenerowane klasy** , więc kliknij przycisk **Zakończ** , aby utworzyć nowy projekt MFC.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Aby utworzyć projekt MFC w programie Visual Studio 2017 lub starszym

1. Użyj **Kreatora aplikacji MFC** , aby utworzyć nową aplikację MFC. Aby uruchomić kreatora, w menu **plik** wybierz pozycję **Nowy**, a następnie wybierz pozycję **projekt**. Zostanie wyświetlone okno dialogowe **Nowy projekt** .

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Wizualizacja C++**  w okienku **typy projektów** , a następnie wybierz pozycję **MFC**. Następnie w okienku **Szablony** wybierz pozycję **aplikacja MFC**. Wpisz nazwę projektu, na przykład, `MFCShellControls` i kliknij przycisk **OK**. 

   Po wyświetleniu **Kreatora aplikacji MFC** należy użyć następujących opcji:

   1. W okienku **Typ aplikacji** w obszarze **Typ aplikacji**wyczyść opcję dokumenty z **kartami** . Następnie wybierz kolejno pozycje **pojedynczy dokument** i **Obsługa architektury dokument/widok**. W obszarze **styl projektu**wybierz pozycję **Visual Studio**, a następnie z listy rozwijanej **styl i kolory wizualizacji** wybierz pozycję **Office 2007 (motyw niebieski)** .

   1. W okienku **Obsługa dokumentu złożonego** zaznacz opcję **Brak**.

   1. Nie wprowadzaj żadnych zmian w okienku **ciągi szablonu dokumentu** .

   1. W okienku **Obsługa bazy danych** (Visual Studio 2015 i starsze) wybierz pozycję **Brak** , ponieważ aplikacja nie korzysta z bazy danych.

   1. W okienku **funkcje interfejsu użytkownika** upewnij się, że jest zaznaczona opcja **Użyj paska menu i paska narzędzi** . Pozostaw wszystkie inne opcje.

   1. W okienku **funkcje zaawansowane** w obszarze **funkcje zaawansowane**zaznacz opcję tylko **kontrolki ActiveX** i **manifest typowej kontroli**. W obszarze **zaawansowane okienka ramki**wybierz tylko opcję **okienka nawigacji** . Spowoduje to, że Kreator utworzy okienko z lewej strony okna z `CMFCShellTreeCtrl` już osadzonym.

   1. Nie będziemy wprowadzać żadnych zmian w okienku **wygenerowane klasy** , więc kliknij przycisk **Zakończ** , aby utworzyć nowy projekt MFC.

::: moniker-end

Sprawdź, czy aplikacja została utworzona pomyślnie, kompilując ją i uruchamiając. Aby skompilować aplikację, w menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom aplikację, wybierając pozycję **Rozpocznij debugowanie** z menu **debugowanie** .

Kreator automatycznie tworzy aplikację, która ma standardowy pasek menu, standardowy pasek narzędzi, standardowy pasek stanu i pasek programu Outlook po lewej stronie okna z widokiem **foldery** i widok **kalendarza** .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Aby dodać kontrolkę lista powłoki do widoku dokumentu

1. W tej sekcji dodasz wystąpienie `CMFCShellListCtrl` do widoku utworzonego przez kreatora. Otwórz plik nagłówkowy widoku przez dwukrotne kliknięcie **MFCShellControlsView. h** w **Eksplorator rozwiązań**.

   Znajdź dyrektywę `#pragma once` znajdującą się w górnej części pliku nagłówkowego. Bezpośrednio poniżej dodaje ten kod, aby dołączyć plik nagłówka dla `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Teraz Dodaj zmienną członkowską typu `CMFCShellListCtrl`. Najpierw zlokalizuj następujący komentarz w pliku nagłówka:

   ```cpp
   // Generated message map functions
   ```

   Bezpośrednio nad tym komentarzem Dodaj następujący kod:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **Kreator aplikacji MFC** utworzył `CMFCShellTreeCtrl` już obiekt w `CMainFrame` klasie, ale jest to chroniony element członkowski. Będziemy uzyskiwać dostęp do obiektu później, dlatego teraz utworzysz metodę dostępu. Otwórz plik nagłówka MainFrm. h, klikając go dwukrotnie w **Eksplorator rozwiązań**. Znajdź następujący komentarz:

   ```cpp
   // Attributes
   ```

   Bezpośrednio pod nim Dodaj następującą deklarację metody:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Następnie otwórz plik źródłowy MainFrm. cpp, klikając go dwukrotnie w **Eksplorator rozwiązań**. W dolnej części tego pliku Dodaj następującą definicję metody:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Teraz aktualizujemy `CMFCShellControlsView` klasę, aby `WM_CREATE` obsłużyć komunikat systemu Windows. Otwórz okno **Widok klasy** i wybierz `CMFCShellControlsView` klasę. Kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**.

   Następnie w [Kreatorze klasy](reference/mfc-class-wizard.md)kliknij kartę **komunikaty** . Przewiń w dół do momentu `WM_CREATE` znalezienia komunikatu. Z listy rozwijanej obok pozycji `WM_CREATE`wybierz pozycję  **\<Dodaj > OnCreate**. Polecenie tworzy program obsługi komunikatów dla nas i automatycznie aktualizuje mapę wiadomości MFC.

   W metodzie teraz utworzysz nasz `CMFCShellListCtrl` obiekt. `OnCreate` Znajdź definicję `OnCreate` metody w pliku źródłowym MFCShellControlsView. cpp i Zastąp jej implementację następującym kodem:

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

1. Powtórz poprzedni krok, ale dla `WM_SIZE` wiadomości. Spowoduje to, że widok aplikacji zostanie narysowany ponownie za każdym razem, gdy użytkownik zmieni rozmiar okna aplikacji. Zastąp definicję dla `OnSize` metody następującym kodem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Ostatnim krokiem jest połączenie `CMFCShellTreeCtrl` obiektów i `CMFCShellListCtrl` przy użyciu metody [CMFCShellTreeCtrl:: SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) . Po wywołaniu `CMFCShellTreeCtrl::SetRelatedList`programu `CMFCShellListCtrl` zostanie automatycznie wyświetlona zawartość elementu wybranego w `CMFCShellTreeCtrl`. Połączymy obiekty w `OnActivateView` metodzie, która została przesłonięta z [CView:: OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   W pliku nagłówkowym MFCShellControlsView. h, wewnątrz `CMFCShellControlsView` deklaracji klasy, Dodaj następującą deklarację metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Następnie Dodaj definicję metody do pliku źródłowego MFCShellControlsView. cpp:

    ```cpp
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView)
    {
        if (bActivate&& AfxGetMainWnd() != NULL)
        {
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);
        }

        CView::OnActivateView(bActivate,
            pActivateView,
            pDeactiveView);
    }
    ```

   Ponieważ wywołujemy metody z `CMainFrame` klasy, należy `#include` dodać dyrektywę w górnej części pliku źródłowego MFCShellControlsView. cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Sprawdź, czy aplikacja została utworzona pomyślnie, kompilując ją i uruchamiając. Aby skompilować aplikację, w menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, wybierając pozycję **Rozpocznij debugowanie** z menu **debugowanie** .

   Należy teraz zobaczyć szczegóły dotyczące elementu wybranego w `CMFCShellTreeCtrl` okienku Widok. Po kliknięciu węzła w programie `CMFCShellTreeCtrl` `CMFCShellListCtrl` zostanie on automatycznie zaktualizowany. Podobnie po dwukrotnym kliknięciu folderu w programie `CMFCShellListCtrl` `CMFCShellTreeCtrl` należy automatycznie zaktualizować.

   Kliknij prawym przyciskiem myszy dowolny element w kontrolce drzewa lub w kontrolce listy. To samo menu kontekstowe jest tak samo, jak w przypadku używania rzeczywistego **Eksploratora plików**.

## <a name="next-steps"></a>Następne kroki

- Kreator utworzył pasek programu Outlook z okienka **foldery** i okienka **Kalendarz** . Prawdopodobnie nie ma sensu okienka **kalendarza** w oknie **Eksploratora** , dlatego Usuń to okienko teraz.

- Obsługuje wyświetlanie plików w różnych trybach, takich jak duże ikony, małe ikony, lista i szczegóły. `CMFCShellListCtrl` Zaktualizuj aplikację w celu zaimplementowania tej funkcji. Wskazówka: zobacz [Visual C++ Samples](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)
