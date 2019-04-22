---
title: 'Przewodnik: Używanie nowych formantów powłoki MFC'
ms.date: 09/20/2018
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: ef0e4856a844503f8d13b7b6ed37318b76b6af69
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772153"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Przewodnik: Używanie nowych formantów powłoki MFC

W tym instruktażu utworzysz aplikację, podobny Eksploratora plików. Utworzysz okno które ma dwa okienka. W okienku po lewej stronie będą przechowywane [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) obiekt, który wyświetla hierarchiczny widok pulpitu. W okienku po prawej stronie będzie przechowywać [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) przedstawiająca pliki w folderze, który wybrano w okienku po lewej stronie.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku przyjęto założenie, że po skonfigurowaniu programu Visual Studio do użycia **ogólnych ustawieniach projektowych**. Jeśli używasz ustawienia tworzenia różnych niektóre okna programu Visual Studio, których używa w tym przewodniku mogą nie być wyświetlane domyślnie.

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>Aby utworzyć nową aplikację MFC przy użyciu Kreatora aplikacji MFC

1. Użyj **Kreator aplikacji MFC** do utworzenia nowej aplikacji MFC. Aby uruchomić kreatora z **pliku** menu wybierz opcję **nowy**, a następnie wybierz pozycję **projektu**. **Nowy projekt** pojawi się okno dialogowe.

1. W **nowy projekt** okna dialogowego rozwiń **Visual C++** w węźle **typów projektów** okienka, a następnie wybierz **MFC**. Następnie w **szablony** okienku wybierz **aplikacji MFC**. Wpisz nazwę dla projektu, takie jak `MFCShellControls` i kliknij przycisk **OK**. Po **Kreator aplikacji MFC** Wyświetla, użyj następujących opcji:

    1. Na **typ aplikacji** okienku w obszarze **typ aplikacji**, wyczyść **dokumenty z zakładkami** opcji. Następnie wybierz pozycję **pojedynczego dokumentu** i wybierz **Obsługa architektury dokument/widok**. W obszarze **projektu styl**, wybierz opcję **programu Visual Studio**i z **styl wizualny i kolory** listy rozwijanej listy wybierz **Office 2007 (motyw niebieski)**.

    1. Na **Obsługa dokumentów złożonych** okienku wybierz **Brak**.

    1. Nie wprowadzaj żadnych zmian do **ciągi szablonu dokumentu** okienka.

    1. Na **obsługi bazy danych** okienko (Visual Studio 2015 i starsze), wybierz **Brak** aplikacja korzysta z bazy danych.

    1. Na **funkcje interfejsu użytkownika** okienka, upewnij się, że **użyj paska menu i paska narzędzi** opcja jest zaznaczona. Pozostaw inne opcje, ponieważ są one.

    1. Na **funkcje zaawansowane** okienku w obszarze **zaawansowane funkcje**, wybierz tylko **formantów ActiveX** i **manifestu wspólnej kontroli**. W obszarze **zaawansowane okienka ramki**, wybierz tylko **okienka nawigacji** opcji. Spowoduje to, że kreatora, aby utworzyć w okienku po lewej stronie okna z `CMFCShellTreeCtrl` już osadzonych.

    1. Użyjemy nie wprowadzaj żadnych zmian w **wygenerowane klasy** okienku, kliknij Tak **Zakończ** do utworzenia Twojego nowego projektu MFC.

1. Sprawdź, czy aplikacja została pomyślnie utworzona, tworząc i uruchamiając go. Aby skompilować aplikację, z **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom aplikację, wybierając **Rozpocznij debugowanie** z **debugowania** menu.

   Kreator automatycznie tworzy aplikację, która ma standardowy pasek menu, standardowy pasek narzędzi, pasek stanu standardowe i paska Outlook po lewej stronie okna z **folderów** widoku i **kalendarza** widoku .

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>Aby dodać formant listy powłoki do widoku dokumentu

1. W tej sekcji dodasz wystąpienie `CMFCShellListCtrl` do widoku, utworzony przez kreatora. Otwórz plik nagłówka w widoku, klikając dwukrotnie **MFCShellControlsView.h** w **Eksploratora rozwiązań**.

   Znajdź `#pragma once` dyrektywę w górnej części pliku nagłówka. Natychmiast poniżej go Dodaj ten kod, aby uwzględnić plik nagłówka dla `CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Teraz Dodaj zmienną składową typu `CMFCShellListCtrl`. Po pierwsze Znajdź poniższy komentarz w pliku nagłówka:

   ```cpp
   // Generated message map functions
   ```

   Bezpośrednio nad tym komentarzem, Dodaj następujący kod:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **Kreator aplikacji MFC** utworzonym `CMFCShellTreeCtrl` obiektu `CMainFrame` klasy, ale jego chroniony element członkowski. Firma Microsoft będzie później uzyskać dostęp do obiektu, dzięki czemu można teraz tworzyć metody dostępu dla niego. Otwórz plik nagłówkowy MainFrm.h, klikając go dwukrotnie **Eksploratora rozwiązań**. Znajdź poniższy komentarz:

   ```cpp
   // Attributes
   ```

   Bezpośrednio pod nim, dodaj następującą deklarację metody:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Następnie otwórz plik źródłowy MainFrm.cpp, klikając go dwukrotnie **Eksploratora rozwiązań**. W dolnej części tego pliku Dodaj następującą definicję metody:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Teraz możemy zaktualizować `CMFCShellControlsView` klasy do obsługi `WM_CREATE` komunikatów systemu windows. Otwórz **Widok klas** okna, a następnie wybierz pozycję `CMFCShellControlsView` klasy. Kliknij prawym przyciskiem myszy i wybierz **właściwości**.

    Następnie w **właściwości** okna, kliknij przycisk **wiadomości** ikony. Przewiń w dół, aż znajdziesz `WM_CREATE` wiadomości. Z listy rozwijanej obok pozycji listy `WM_CREATE`, wybierz opcję  **\<Dodaj > OnCreate**. Polecenie tworzy program obsługi komunikatów dla nas i automatycznie aktualizuje mapy komunikatów MFC.

   W `OnCreate` metody, utworzymy teraz naszych `CMFCShellListCtrl` obiektu. Znajdź `OnCreate` definicji metody w MFCShellControlsView.cpp pliku źródłowego i zastąp jego implementacja następującym kodem:

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

1. Powtórz poprzedni krok, ale w przypadku `WM_SIZE` wiadomości. Spowoduje widoku aplikacji narysowania zawsze wtedy, gdy użytkownik zmieni rozmiar okna aplikacji. Zastąp definicję dla `OnSize` metoda następującym kodem:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Ostatni krok polega na połączeniu `CMFCShellTreeCtrl` i `CMFCShellListCtrl` obiektów przy użyciu [CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) metody. Po wywołaniu metody `CMFCShellTreeCtrl::SetRelatedList`, `CMFCShellListCtrl` zostanie automatycznie wyświetlona zawartość elementu wybranego w `CMFCShellTreeCtrl`. Łączymy obiektów w `OnActivateView` metody, która zostanie zastąpiona z [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview).

   W pliku nagłówkowym MFCShellControlsView.h wewnątrz `CMFCShellControlsView` deklaracji klasy, dodaj następującą deklarację metody:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Następnie dodaj definicję dla metody MFCShellControlsView.cpp pliku źródłowego:

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

   Ponieważ Zadzwonimy pod numer telefonu metody z `CMainFrame` klasy, możemy dodać `#include` dyrektywę w górnej części pliku źródłowego MFCShellControlsView.cpp:

    ```cpp
    #include "MainFrm.h"
    ```

1. Sprawdź, czy aplikacja została pomyślnie utworzona, tworząc i uruchamiając go. Aby skompilować aplikację, z **kompilacji** menu wybierz opcję **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom go, wybierając **Rozpocznij debugowanie** z **debugowania** menu.

   Zostaną wyświetlone szczegóły dotyczące elementu zaznaczonego w `CMFCShellTreeCtrl` w okienku widoku. Po kliknięciu węzła w `CMFCShellTreeCtrl`, `CMFCShellListCtrl` zostaną automatycznie zaktualizowane. Podobnie jeśli klikniesz dwukrotnie folder, w `CMFCShellListCtrl`, `CMFCShellTreeCtrl` powinny być aktualizowane automatycznie.

   Kliknij prawym przyciskiem myszy dowolny element w drzewie lub kontrolki listy. Pobieranie tego samego menu kontekstowego tak, jakby były używane rzeczywiste **Eksploratora plików**.

## <a name="next-steps"></a>Następne kroki

- Kreator utworzył paska Outlook zarówno **folderów** okienka i **kalendarza** okienka. Prawdopodobnie nie ma sensu ma **kalendarza** okienka **Explorer** okna, więc teraz usunąć okienka.

- `CMFCShellListCtrl` Obsługuje wyświetlanie plików w różnych trybach, takich jak **duże ikony**, **małe ikony**, **listy**, i **szczegóły**. Zaktualizuj aplikację w celu zaimplementowania tej funkcji. Wskazówka: zobacz [przykłady Visual C++](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)
