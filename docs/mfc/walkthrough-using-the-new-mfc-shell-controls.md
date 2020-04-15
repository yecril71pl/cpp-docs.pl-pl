---
title: 'Wskazówki: używanie nowych formantów powłoki MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 5786fbbf7ec9f31e7d895a96dae27b8fc95abda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360210"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Wskazówki: używanie nowych formantów powłoki MFC

W tym instruktażu utworzysz aplikację podobną do Eksploratora plików. Utworzysz okno, które ma dwa okienka. Lewe okienko będzie zawierać [OBIEKT CMFCShellTreeCtrl,](../mfc/reference/cmfcshelltreectrl-class.md) który wyświetla pulpit w widoku hierarchicznym. W prawym okienku będzie przechowywać [CMFCShellListCtrl,](../mfc/reference/cmfcshelllistctrl-class.md) który pokazuje pliki w folderze, który jest zaznaczony w lewym okienku.

## <a name="prerequisites"></a>Wymagania wstępne

- W programie Visual Studio 2017 i nowszych obsługa MFC jest składnikiem opcjonalnym. Aby go zainstalować, otwórz Instalatora programu Visual Studio z menu Start systemu Windows. Znajdź wersję używanego programu Visual Studio i wybierz przycisk **Modyfikuj.** Upewnij się, że **programowanie pulpitu z** kafelkiem C++ jest zaznaczone. W obszarze **Składniki opcjonalne**sprawdź przycisk **Wsparcia MFC.**

- W tym przewodniku przyjęto założenie, że program Visual Studio został skonfigurowany do **używania ogólnych ustawień rozwoju**. Jeśli używasz innego ustawienia rozwoju, niektóre okna programu Visual Studio, których używamy w tym instruktażu, mogą nie być wyświetlane domyślnie.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Aby utworzyć nową aplikację MFC przy użyciu Kreatora aplikacji MFC

Te kroki różnią się w zależności od używanej wersji programu Visual Studio. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>Aby utworzyć projekt MFC w programie Visual Studio 2019

1. Z menu głównego wybierz polecenie **Plik** > **nowego** > **projektu,** aby otworzyć okno **dialogowe Tworzenie nowego projektu.**

1. W polu wyszukiwania u góry wpisz **MFC,** a następnie wybierz **aplikację MFC** z listy wyników.

1. Kliknij przycisk **Dalej**. Na następnej stronie wprowadź nazwę projektu i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt.

   Po wyświetleniu **Kreatora aplikacji MFC** użyj następujących opcji:

   1. Po lewej stronie wybierz **pozycję Typ aplikacji.** Następnie wybierz **pojedynczy dokument** i wybierz pozycję Obsługa **architektury Dokumentu/widoku**. W obszarze **Styl projektu**wybierz pozycję **Visual Studio**, a z listy rozwijanej Styl i kolory **wizualne** wybierz pozycję **Office 2007 (motyw Niebieski).**

   1. W okienku **Obsługa dokumentów złożonych** wybierz pozycję **Brak**.

   1. Nie wprowadzać żadnych zmian w okienku **Właściwości szablonu dokumentu.**

   1. W okienku **Funkcje interfejsu użytkownika** upewnij się, że jest zaznaczona opcja **Użyj paska menu i paska narzędzi.** Pozostaw wszystkie inne opcje w jakim są.

   1. W okienku **Funkcje zaawansowane** wybierz pozycję **Kontrolki ActiveX**, **Wspólny manifest sterowania**i **Okienko nawigacji.** Zostaw wszystko inne, jak to jest. Opcja **Okienko nawigacji** spowoduje, że kreator utworzy okienko po `CMFCShellTreeCtrl` lewej stronie okna z już osadzonym.

   1. Nie zamierzamy wprowadzać żadnych zmian w okienku **Wygenerowane klasy,** więc kliknij przycisk **Zakończ,** aby utworzyć nowy projekt MFC.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>Aby utworzyć projekt MFC w programie Visual Studio 2017 lub starszym

1. Kreator **aplikacji MFC** służy do tworzenia nowej aplikacji MFC. Aby uruchomić kreatora, z menu **Plik** wybierz pozycję **Nowy**, a następnie wybierz pozycję **Projekt**. Zostanie wyświetlone okno dialogowe **Nowy projekt.**

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual C++** w okienku **Typy projektu** i wybierz pozycję **MFC**. Następnie w okienku **Szablony** wybierz pozycję **Aplikacja MFC**. Wpisz nazwę projektu, na `MFCShellControls` przykład i kliknij przycisk **OK**.

   Po wyświetleniu **Kreatora aplikacji MFC** użyj następujących opcji:

   1. W okienku **Typ aplikacji** w obszarze **Typ aplikacji**wyczyść opcję Dokumenty **z kartami.** Następnie wybierz **pozycję Pojedynczy dokument** i wybierz pozycję Obsługa architektury **Dokumentu/widoku**. W obszarze **Styl projektu**wybierz pozycję **Visual Studio**, a z listy rozwijanej Styl i kolory **wizualne** wybierz pozycję **Office 2007 (motyw Niebieski).**

   1. W okienku **Obsługa dokumentów złożonych** wybierz pozycję **Brak**.

   1. Nie wprowadzać żadnych zmian w okienku **Ciągi szablonów dokumentów.**

   1. W okienku **Obsługa bazy danych** (Visual Studio 2015 i starsze) wybierz opcję **Brak,** ponieważ aplikacja nie korzysta z bazy danych.

   1. W okienku **Funkcje interfejsu użytkownika** upewnij się, że jest zaznaczona opcja **Użyj paska menu i paska narzędzi.** Pozostaw wszystkie inne opcje w jakim są.

   1. W okienku **Funkcje zaawansowane** w obszarze **Funkcje zaawansowane**wybierz tylko **formanty ActiveX** i **Manifest wspólnej kontroli**. W **obszarze Okienka ramek zaawansowane**wybierz tylko opcję **Okienko nawigacji.** Spowoduje to, że kreator utworzy okienko po lewej `CMFCShellTreeCtrl` stronie okna z już osadzonym.

   1. Nie zamierzamy wprowadzać żadnych zmian w okienku **Wygenerowane klasy,** więc kliknij przycisk **Zakończ,** aby utworzyć nowy projekt MFC.

::: moniker-end

Sprawdź, czy aplikacja została pomyślnie utworzona przez jej utworzenie i uruchomienie. Aby utworzyć aplikację, z menu **Kompilacja** wybierz opcję **Buduj rozwiązanie**. Jeśli aplikacja tworzy pomyślnie, uruchom aplikację, wybierając **polecenie Rozpocznij debugowanie** z menu **debugowania.**

Kreator automatycznie tworzy aplikację ze standardowym paskiem menu, standardowym paskiem narzędzi, standardowym paskiem stanu i paskiem programu Outlook po lewej stronie okna z widokiem **Foldery** i widokiem **kalendarza.**

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Aby dodać kontrolka listy powłoki do widoku dokumentu

1. W tej sekcji dodasz wystąpienie `CMFCShellListCtrl` do widoku utworzonego przez kreatora. Otwórz plik nagłówka widoku, klikając dwukrotnie **MFCShellControlsView.h** w **Eksploratorze rozwiązań**.

   Zlokalizuj `#pragma once` dyrektywę w górnej części pliku nagłówka. Bezpośrednio pod nim dodać ten kod, `CMFCShellListCtrl`aby dołączyć plik nagłówka dla:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Teraz dodaj zmienną `CMFCShellListCtrl`członkowną typu . Najpierw znajdź następujący komentarz w pliku nagłówka:

   ```cpp
   // Generated message map functions
   ```

   Bezpośrednio powyżej tego komentarza, dodaj ten kod:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **Kreator aplikacji MFC** już `CMFCShellTreeCtrl` utworzył `CMainFrame` obiekt w klasie, ale jest chronionym elementem członkowskim. Uzyskamy dostęp do obiektu później, więc utwórz dla niego akcesor teraz. Otwórz plik nagłówka MainFrm.h, klikając go dwukrotnie w **Eksploratorze rozwiązań**. Znajdź następujący komentarz:

   ```cpp
   // Attributes
   ```

   Natychmiast pod nim dodać następującą deklarację metody:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Następnie otwórz plik źródłowy MainFrm.cpp, klikając go dwukrotnie w **Eksploratorze rozwiązań**. U dołu tego pliku dodaj następującą definicję metody:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Teraz aktualizujemy `CMFCShellControlsView` klasy `WM_CREATE` do obsługi wiadomości systemu Windows. Otwórz okno **Widok klasy** `CMFCShellControlsView` i wybierz klasę. Kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

   Następnie w [Kreatorze zajęć](reference/mfc-class-wizard.md)kliknij kartę **Wiadomości.** `WM_CREATE` Przewiń w dół, aż znajdziesz wiadomość. Z listy rozwijanej obok `WM_CREATE`pozycji Wybierz pozycję ** \<Dodaj> OnCreate**. Polecenie tworzy dla nas program obsługi wiadomości i automatycznie aktualizuje mapę komunikatów MFC.

   W `OnCreate` metodzie utworzymy teraz `CMFCShellListCtrl` nasz obiekt. Znajdź `OnCreate` definicję metody w pliku źródłowym MFCShellControlsView.cpp i zastąp jego implementację następującym kodem:

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

1. Powtórz poprzedni krok, `WM_SIZE` ale dla wiadomości. Spowoduje to, że widok aplikacji zostanie ponownie narysowany, gdy użytkownik zmieni rozmiar okna aplikacji. Zastąp `OnSize` definicję metody następującym kodem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Ostatnim krokiem jest `CMFCShellTreeCtrl` połączenie `CMFCShellListCtrl` i obiektów przy użyciu [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) metody. Po wywołaniu `CMFCShellTreeCtrl::SetRelatedList` `CMFCShellListCtrl` program automatycznie wyświetli zawartość elementu wybranego `CMFCShellTreeCtrl`w pliku . Łączymy obiekty w `OnActivateView` metodzie, która jest zastąpiona z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   W pliku nagłówka MFCShellControlsView.h `CMFCShellControlsView` wewnątrz deklaracji klasy dodaj następującą deklarację metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Następnie dodaj definicję metody do pliku źródłowego MFCShellControlsView.cpp:

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

   Ponieważ wywołujemy metody z `CMainFrame` klasy, musimy `#include` dodać dyrektywę w górnej części pliku źródłowego MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Sprawdź, czy aplikacja została pomyślnie utworzona przez jej utworzenie i uruchomienie. Aby utworzyć aplikację, z menu **Kompilacja** wybierz opcję **Buduj rozwiązanie**. Jeśli aplikacja tworzy pomyślnie, uruchom ją, wybierając **polecenie Rozpocznij debugowanie** z menu **Debugowania.**

   Teraz powinieneś zobaczyć szczegóły elementu wybranego `CMFCShellTreeCtrl` w okienku widoku. Po kliknięciu węzła `CMFCShellTreeCtrl`w `CMFCShellListCtrl` , zostanie automatycznie zaktualizowany. Podobnie, jeśli klikniesz dwukrotnie `CMFCShellListCtrl`folder `CMFCShellTreeCtrl` w polu , powinien zostać automatycznie zaktualizowany.

   Kliknij prawym przyciskiem myszy dowolny element w formancie drzewa lub w formancie listy. Otrzymujesz to samo menu kontekstowe, jak w przypadku korzystania z prawdziwego **Eksploratora plików**.

## <a name="next-steps"></a>Następne kroki

- Kreator utworzył pasek programu Outlook z okienkiem **Foldery** i okienkiem **Kalendarz.** Prawdopodobnie nie ma sensu mieć **okienka Kalendarz** w oknie **Eksploratora,** więc usuń teraz to okienko.

- Obsługuje `CMFCShellListCtrl` wyświetlanie plików w różnych trybach, takich jak **Duże ikony,** **Małe ikony**, **Lista**i **Szczegóły**. Zaktualizuj aplikację, aby zaimplementować tę funkcję. Wskazówka: zobacz [Przykłady języka Visual C++](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Wskazówki](../mfc/walkthroughs-mfc.md)
